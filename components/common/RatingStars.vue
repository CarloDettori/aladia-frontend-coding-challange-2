<script setup lang="ts">
import { computed } from 'vue'

const props = withDefaults(
  defineProps<{
    value: number
    max?: number
    size?: 'sm' | 'md' | 'lg'
  }>(),
  {
    max: 5,
    size: 'md'
  }
)

const fullStars = computed(() => Math.floor(props.value))
const hasHalfStar = computed(() => props.value % 1 >= 0.5)
const emptyStars = computed(() => {
  return props.max - fullStars.value - (hasHalfStar.value ? 1 : 0)
})

const sizeClass = computed(() => {
  switch (props.size) {
    case 'sm':
      return 'text-sm'
    case 'lg':
      return 'text-xl'
    default:
      return 'text-base'
  }
})
</script>

<template>
  <div
    class="inline-flex items-center gap-0.5 text-amber-500"
    :class="sizeClass"
    role="img"
    :aria-label="`Rating: ${value} out of ${max} stars`"
  >
    <!-- full stars -->
    <span v-for="n in fullStars" :key="'full-' + n">★</span>

    <!-- half star -->
    <span v-if="hasHalfStar">☆</span>

    <!-- empty stars -->
    <span v-for="n in emptyStars" :key="'empty-' + n" class="text-slate-300">
      ★
    </span>
  </div>
</template>
