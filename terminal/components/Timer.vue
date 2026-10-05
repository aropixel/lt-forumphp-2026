<script setup lang="ts">
import { onBeforeUnmount, ref, watch } from 'vue'
import { useIsSlideActive, useSlideContext } from '@slidev/client'

// Chronomètre qui monte de `from` à `to` secondes, seconde par seconde, en `duration` ms, à l'entrée de la slide.
// Hors présentation (aperçu, export PDF), il affiche directement la valeur finale.
const props = withDefaults(defineProps<{
  from?: number
  to: number
  delay?: number
  duration?: number
  unit?: string
}>(), {
  from: 0,
  delay: 0,
  duration: 2000,
  unit: 's',
})

const { $renderContext } = useSlideContext()
const animated = ['slide', 'presenter'].includes($renderContext.value)
const isActive = useIsSlideActive()

const elapsed = ref(animated ? props.from : props.to)
const done = ref(!animated)
let frame = 0
let timeout = 0

function stop() {
  cancelAnimationFrame(frame)
  clearTimeout(timeout)
}

// Remet le chrono à zéro : au retour sur la slide, il ne doit jamais
// réafficher la valeur où on l'avait laissé.
function reset() {
  stop()
  elapsed.value = props.from
  done.value = false
}

function start() {
  reset()
  timeout = window.setTimeout(() => {
    const t0 = performance.now()
    const tick = (now: number) => {
      // L'horodatage du premier frame peut précéder t0 : on ne descend jamais sous `from`.
      const progress = Math.max(0, (now - t0) / props.duration)
      elapsed.value = Math.min(props.from + Math.floor(progress * (props.to - props.from)), props.to)
      if (elapsed.value < props.to)
        frame = requestAnimationFrame(tick)
      else
        done.value = true
    }
    frame = requestAnimationFrame(tick)
  }, props.delay)
}

if (animated) {
  watch(isActive, active => {
    if (active)
      return start()
    // En quittant, on attend que la slide soit masquée pour ne pas voir le retour à zéro.
    stop()
    timeout = window.setTimeout(reset, 200)
  }, { immediate: true })
}

onBeforeUnmount(stop)
</script>

<template>
  <span class="timer" :class="{ 'timer-done': done }">{{ elapsed }} {{ props.unit }}</span>
</template>
