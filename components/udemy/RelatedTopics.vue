<script setup lang="ts">
import CommonSection from '~/components/common/Section.vue'
import CommonSectionTitle from '~/components/common/SectionTitle.vue'

const topics = [
  'Python',
  'Data Science',
  'Machine Learning',
  'Web Development',
  'Flask',
  'Automation',
  'Pandas',
  'NumPy'
]
</script>

<template>
  <CommonSection>
    <div>
      <CommonSectionTitle title="Argomenti correlati" />

      <ul class="mt-4 flex flex-wrap gap-2" aria-label="Related topics">
        <li v-for="t in topics" :key="t">
          <a
            href="#"
            class="inline-flex items-center rounded-full border border-slate-300 bg-white px-3 py-1 text-sm font-semibold text-slate-800 hover:bg-slate-50"
          >
            {{ t }}
          </a>
        </li>
      </ul>
    </div>
  </CommonSection>
</template>