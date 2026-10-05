<script setup lang="ts">
defineProps<{
  value?: string
  label?: string
  caption?: string
  tone?: 'red' | 'faint' | 'green' | 'muted'
  labelTone?: 'red' | 'faint' | 'green' | 'muted'
}>()
</script>

<template>
  <div class="stat">
    <span class="stat-label" :class="labelTone ? `tone-${labelTone}` : ''">{{ label }}</span>
    <span class="stat-value" :class="tone ? `tone-${tone}` : ''"><slot>{{ value }}</slot></span>
    <span class="stat-caption">{{ caption }}</span>
  </div>
</template>
