<script setup lang="ts">
import { computed, ref } from 'vue'
import Section from '~/components/common/Section.vue'
import SectionTitle from '~/components/common/SectionTitle.vue'

type Lesson = {
  title: string
  duration: string
}

type CurriculumSection = {
  title: string
  lectures: number
  duration: string
  lessons: Lesson[]
}

const sections = ref<CurriculumSection[]>([
  {
    title: 'Getting Started',
    lectures: 6,
    duration: '39min',
    lessons: [
      { title: 'Welcome to the course', duration: '3:12' },
      { title: 'How to get the most out of this course', duration: '6:40' },
      { title: 'Installing Python', duration: '9:10' }
    ]
  },
  {
    title: 'Variables & Data Types',
    lectures: 10,
    duration: '1hr 12min',
    lessons: [
      { title: 'Variables in Python', duration: '8:01' },
      { title: 'Strings and Numbers', duration: '10:44' },
      { title: 'Type conversions', duration: '7:36' }
    ]
  },
  {
    title: 'Control Flow',
    lectures: 12,
    duration: '1hr 30min',
    lessons: [
      { title: 'If/Else & Comparison Operators', duration: '11:20' },
      { title: 'Loops: for & while', duration: '12:05' },
      { title: 'Mini project: Password Generator', duration: '18:55' }
    ]
  },
  {
    title: 'Functions & Scope',
    lectures: 9,
    duration: '1hr 05min',
    lessons: [
      { title: 'Defining functions', duration: '9:48' },
      { title: 'Parameters & return values', duration: '11:02' },
      { title: 'Local vs global scope', duration: '8:27' }
    ]
  }
])

const openIndex = ref<number>(0)

const toggle = (index: number) => {
  openIndex.value = openIndex.value === index ? -1 : index
}

const summary = computed(() => {
  const totalSections = sections.value.length
  const totalLectures = sections.value.reduce((acc, s) => acc + s.lectures, 0)
  // durata totale statica “fake” ma credibile
  return `${totalSections} sezioni • ${totalLectures} lezioni • 52 h 03 min di durata totale`
})
</script>

<template>
  <Section>
    <div>
      <SectionTitle title="Contenuti del corso" />
      <p class="text-sm text-slate-600">{{ summary }}</p>

      <div
        class="mt-4 overflow-hidden rounded-xl border border-slate-200 bg-white"
      >
        <div
          v-for="(section, index) in sections"
          :key="section.title"
          class="border-b border-slate-200 last:border-b-0"
        >
          <h3>
            <button
              type="button"
              class="flex w-full items-center justify-between gap-4 px-5 py-4 text-left hover:bg-slate-50"
              :aria-expanded="openIndex === index"
              :aria-controls="`curriculum-panel-${index}`"
              @click="toggle(index)"
            >
              <div class="min-w-0">
                <div class="truncate font-semibold text-slate-900">
                  {{ section.title }}
                </div>
                <div class="mt-1 text-xs text-slate-600">
                  {{ section.lectures }} lezioni • {{ section.duration }}
                </div>
              </div>

              <span
                aria-hidden="true"
                class="shrink-0 text-slate-600 transition"
                :class="openIndex === index ? 'rotate-180' : ''"
              >
                ▾
              </span>
            </button>
          </h3>

          <div
            :id="`curriculum-panel-${index}`"
            v-show="openIndex === index"
            class="px-5 pb-4"
          >
            <ul class="space-y-2">
              <li
                v-for="lesson in section.lessons"
                :key="lesson.title"
                class="flex items-start justify-between gap-4 text-sm text-slate-700"
              >
                <div class="flex min-w-0 items-start gap-3">
                  <span aria-hidden="true" class="mt-0.5 text-slate-500"
                    >▶</span
                  >
                  <span class="truncate">{{ lesson.title }}</span>
                </div>
                <span class="shrink-0 text-xs text-slate-500">{{
                  lesson.duration
                }}</span>
              </li>
            </ul>

            <button
              type="button"
              class="mt-4 text-sm font-semibold text-violet-700 hover:underline"
            >
              Mostra tutte le lezioni
            </button>
          </div>
        </div>
      </div>
    </div>
  </Section>
</template>
