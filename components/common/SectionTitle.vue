<script setup lang="ts">
defineProps<{ title: string; subtitle?: string }>()
</script>

<template>
  <header class="mb-4">
    <h2 class="text-2xl font-extrabold text-slate-900">{{ title }}</h2>
    <p v-if="subtitle" class="mt-1 text-slate-600">{{ subtitle }}</p>
  </header>
</template>