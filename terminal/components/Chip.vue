<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  who: string
  lower?: boolean
}>()

const names: Record<string, string> = { joel: 'Joël', bastien: 'Bastien' }
const label = computed(() => {
  const name = names[props.who] ?? props.who
  return props.lower ? name.toLowerCase() : name
})
</script>

<template>
  <span class="chip" :class="`chip-${who}`"><slot>{{ label }}</slot></span>
</template>
