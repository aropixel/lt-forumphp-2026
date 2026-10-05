<script setup lang="ts">
defineProps<{
  level: 'WARN' | 'ERROR' | 'FATAL'
  label: string
  detail?: string
  past?: boolean
}>()
</script>

<template>
  <div v-if="past" class="log log-past">
    <span>[{{ level }}]</span><span>{{ label }}</span>
  </div>
  <div v-else class="log">
    <span class="log-level" :class="`log-${level.toLowerCase()}`">[{{ level }}]</span>
    <span><mark>{{ label }}</mark> <span class="muted">— {{ detail }}</span></span>
  </div>
</template>
