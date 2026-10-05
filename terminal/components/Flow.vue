<script setup lang="ts">
defineProps<{
  steps: string[]
  more?: boolean
}>()
</script>

<template>
  <div class="flow">
    <template v-for="(step, i) in steps" :key="i">
      <span v-if="i > 0" class="flow-arrow">→</span>
      <span class="box">{{ step }}</span>
    </template>
    <span v-if="more" class="flow-arrow">…</span>
  </div>
</template>
