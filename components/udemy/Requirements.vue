<script setup lang="ts">
import { computed, ref } from 'vue'

type RequirementItem = string

const props = withDefaults(
  defineProps<{
    title?: string
    intro?: string
    items?: RequirementItem[]
    previewCount?: number
  }>(),
  {
    title: 'Requisiti',
    intro:
      'Welcome to the 100 Days of Code - The Complete Python Pro Bootcamp, the only course you need to learn to code with Python.',
    items: () => [
      "No programming experience needed - I'll teach you everything you need to know",
      'A 64-bit Mac or PC computer with 4GB of memory and access to the internet',
      "No paid software required - I'll teach you how to use PyCharm, Jupyter Notebooks and Google Colab",
      "I'll walk you through, step-by-step how to get all the software installed and set up",
      // “extra” (visibili solo dopo expand)
      'The course is taught by the lead instructor at the App Brewery, London’s best in-person programming Bootcamp.',
      'The course has been updated and you’ll be learning the latest tools and technologies used at large companies.',
      'This course doesn’t cut any corners; there are beautiful animated explanation videos and real-world projects.',
      'The curriculum was developed over a period of 2 years, with comprehensive student testing and feedback.',
      'We’ve taught over 600,000 students how to code and many have gone on to change their lives by becoming developers.',
      'You’ll save yourself over $12,000 by enrolling, and still get access to the same teaching materials.'
    ],
    previewCount: 4
  }
)

const expanded = ref(false)

const visibleItems = computed(() => {
  if (expanded.value) return props.items
  return props.items.slice(0, props.previewCount)
})

const panelId = 'requirements-panel'
</script>

<template>
  <section class="py-6">
    <h2 class="text-2xl font-bold text-slate-900">{{ title }}</h2>

    <p class="mt-3 max-w-3xl text-sm leading-6 text-slate-700">
      {{ intro }}
    </p>

    <div :id="panelId" class="mt-4">
      <ul class="list-disc space-y-2 pl-5 text-sm text-slate-700">
        <li v-for="(item, idx) in visibleItems" :key="idx">
          {{ item }}
        </li>
      </ul>

      <!-- “Mostra di più / Mostra meno” -->
      <button
        type="button"
        class="mt-4 inline-flex items-center gap-2 rounded-md px-2 py-1 text-sm font-semibold text-violet-700 hover:bg-violet-50"
        :aria-expanded="expanded"
        :aria-controls="panelId"
        @click="expanded = !expanded"
      >
        <span>{{ expanded ? 'Mostra meno' : 'Mostra di più' }}</span>
        <span aria-hidden="true" class="text-base">
          {{ expanded ? '▴' : '▾' }}
        </span>
      </button>
    </div>
  </section>
</template>
