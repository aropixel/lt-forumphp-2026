<script setup lang="ts">
import TerminalBar from '../components/TerminalBar.vue'

defineProps<{
  section?: string
  speakers?: string[]
}>()
</script>

<template>
  <div class="slidev-layout term term-cover">
    <TerminalBar :section="section" :speakers="speakers" />
    <div class="term-body">
      <slot />
    </div>
  </div>
</template>
