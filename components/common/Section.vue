<script></script>
<script setup lang="ts">
withDefaults(
  defineProps<{
    as?: 'section' | 'div'
    padded?: boolean
  }>(),
  { as: 'section', padded: true }
)
</script>

<template>
  <component :is="as" :class="[padded ? 'py-10' : '']">
    <slot />
  </component>
</template>
