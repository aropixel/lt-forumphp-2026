<script setup lang="ts">
import TerminalBar from '../components/TerminalBar.vue'

defineProps<{
  section?: string
  speakers?: string[]
  dark?: boolean
}>()
</script>

<template>
  <div class="slidev-layout term term-statement" :class="{ 'term-dark': dark }">
    <TerminalBar :section="section" :speakers="speakers" />
    <div class="term-body">
      <slot />
    </div>
  </div>
</template>
