<script setup lang="ts">
import { computed } from 'vue'

const props = withDefaults(
  defineProps<{
    variant?: 'dark' | 'light'
  }>(),
  { variant: 'dark' }
)

const isDark = computed(() => props.variant === 'dark')

const breadcrumbs = ['Sviluppo', 'Linguaggi di programmazione', 'Python']
const title = '100 Days of Code™: The Complete Python Pro Bootcamp'
const subtitle =
  'Master Python by building 100 projects in 100 days. Learn data science, automation, build websites, games and apps!'
const instructor = 'Dr. Angela Yu, Developer and Lead Instructor'
const lastUpdated = '02/2026'
const language = 'Inglese'
const captions = 'Arabo [Auto], Bulgaro [Auto], Altri 29'
const ratingValue = '4,7'
const ratingCount = '414.294'
const studentsCount = '1.745.088'
</script>

<template>
  <!-- No background here: background comes from PageLayout -->
  <section :class="[isDark ? 'text-white' : 'text-slate-900', 'py-8 lg:py-10']">
    <!-- breadcrumb -->
    <nav :class="[isDark ? 'text-slate-300' : 'text-slate-600', 'text-sm']" aria-label="Breadcrumb">
      <ol class="flex flex-wrap items-center gap-2">
        <li v-for="(item, i) in breadcrumbs" :key="item" class="flex items-center gap-2">
          <span v-if="i !== 0" :class="isDark ? 'text-violet-300' : 'text-slate-400'">›</span>
          <a href="#" class="hover:underline">{{ item }}</a>
        </li>
      </ol>
    </nav>

    <h1 class="mt-4 text-4xl font-extrabold tracking-tight sm:text-5xl">
      {{ title }}
    </h1>

    <p :class="[isDark ? 'text-slate-200' : 'text-slate-700', 'mt-4 max-w-3xl text-lg']">
      {{ subtitle }}
    </p>

    <div class="mt-5 flex flex-wrap items-center gap-3">
      <span class="inline-flex items-center rounded-md bg-emerald-200 px-3 py-1 text-sm font-semibold text-slate-900">
        Best seller
      </span>
      <span class="inline-flex items-center rounded-md bg-amber-200 px-3 py-1 text-sm font-semibold text-slate-900">
        Valutazioni più alte
      </span>

      <div class="flex flex-wrap items-center gap-2 text-sm">
        <span class="font-semibold text-amber-300">{{ ratingValue }}</span>
        <span aria-label="Rating stars" class="text-amber-300">★★★★★</span>
        <a href="#" class="text-violet-300 hover:underline">({{ ratingCount }} valutazioni)</a>
        <span :class="isDark ? 'text-slate-300' : 'text-slate-400'">•</span>
        <span :class="isDark ? 'text-slate-200' : 'text-slate-700'">{{ studentsCount }} studenti</span>
      </div>
    </div>

    <p :class="[isDark ? 'text-slate-200' : 'text-slate-700', 'mt-4 text-sm']">
      Creato da
      <a href="#" class="text-violet-300 hover:underline">{{ instructor }}</a>
    </p>

    <ul :class="[isDark ? 'text-slate-200' : 'text-slate-700', 'mt-4 flex flex-wrap items-center gap-x-6 gap-y-2 text-sm']">
      <li class="inline-flex items-center gap-2">
        <span aria-hidden="true">🗓️</span>
        <span>Ultimo aggiornamento in data {{ lastUpdated }}</span>
      </li>
      <li class="inline-flex items-center gap-2">
        <span aria-hidden="true">🌐</span>
        <span>{{ language }}</span>
      </li>
      <li class="inline-flex items-center gap-2">
        <span aria-hidden="true">💬</span>
        <a href="#" class="text-violet-300 hover:underline">{{ captions }}</a>
      </li>
    </ul>

    <!-- Premium bar -->
    <div class="mt-8 overflow-hidden rounded-xl border border-slate-200 bg-white text-slate-900 shadow-sm">
      <div class="flex flex-col sm:flex-row">
        <div class="flex items-center gap-3 bg-violet-700 px-6 py-4 text-white sm:w-48">
          <span class="text-xl">✅</span>
          <span class="text-lg font-bold">Premium</span>
        </div>

        <div class="flex flex-1 items-center justify-between gap-6 px-6 py-4">
          <p class="text-sm text-slate-700">
            Ottieni l'accesso a oltre 26.850 corsi più votati con Piano individuale Udemy.
          </p>

          <div class="hidden items-center gap-10 sm:flex">
            <div class="text-center">
              <div class="text-xl font-extrabold">{{ ratingValue }}</div>
              <div class="text-xs text-slate-500">{{ ratingCount }} valutazioni</div>
            </div>
            <div class="text-center">
              <div class="text-xl font-extrabold">{{ studentsCount }}</div>
              <div class="text-xs text-slate-500">studenti</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
