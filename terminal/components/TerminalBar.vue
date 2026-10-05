<script setup lang="ts">
import { useSlideContext } from '@slidev/client'
import { computed } from 'vue'
import Chip from './Chip.vue'

defineProps<{
  section?: string
  speakers?: string[]
}>()

const { $page, $nav } = useSlideContext()
const progress = computed(() => `${Math.round(($page.value / $nav.value.total) * 100)}%`)
</script>

<template>
  <div class="term-bar">
    <span class="term-bar-section">[aropixel] {{ section }}</span>
    <span class="term-bar-right">
      <Chip v-for="who in speakers ?? []" :key="who" :who="who" lower />
      <span class="term-progress" aria-hidden="true">
        <span class="term-progress-fill" :style="{ width: progress }" />
      </span>
    </span>
  </div>
</template>
