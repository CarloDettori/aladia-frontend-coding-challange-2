<script setup lang="ts">
import Section from '~/components/common/Section.vue'
import SectionTitle from '~/components/common/SectionTitle.vue'

const items = [
  'You will master the Python programming language by building 100 unique projects over 100 days.',
  'You will learn automation, game, app and web development, data science and machine learning all using Python.',
  'You will be able to program in Python professionally',
  'You will learn Selenium, Beautiful Soup, Requests, Flask, Pandas, NumPy, Scikit Learn, Plotly, and Matplotlib.',
  'Create a portfolio of 100 Python projects to apply for developer jobs',
  'Be able to build fully fledged websites and web apps with Python.'
]
</script>

<template>
  <Section>
    <div class="rounded-xl border border-slate-200 bg-white p-6 shadow-sm">
      <SectionTitle title="Cosa imparerai" />

      <ul class="mt-4 grid gap-4 sm:grid-cols-2" aria-label="Learning outcomes">
        <li v-for="text in items" :key="text" class="flex gap-3">
          <span aria-hidden="true" class="mt-1 text-slate-700">✓</span>
          <p class="text-sm leading-relaxed text-slate-700">
            {{ text }}
          </p>
        </li>
      </ul>
    </div>
  </Section>
</template>
