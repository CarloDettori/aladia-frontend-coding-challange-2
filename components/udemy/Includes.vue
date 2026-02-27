<script setup lang="ts">
import Section from '~/components/common/Section.vue'
import SectionTitle from '~/components/common/SectionTitle.vue'

const left = [
  '52 ore di video on-demand',
  '23 esercizi di codifica',
  'Compiti',
  '232 articoli'
]
const right = [
  '167 risorse scaricabili',
  'Accesso su dispositivo mobile e TV',
  'Sottotitoli',
  'Certificato di completamento'
]
</script>

<template>
  <Section>
    <div>
      <SectionTitle title="Questo corso include:" />

      <div class="grid gap-6 sm:grid-cols-2">
        <ul class="space-y-3" aria-label="Course includes left column">
          <li v-for="item in left" :key="item" class="flex items-start gap-3 text-slate-700">
            <span aria-hidden="true">▸</span>
            <span class="text-sm">{{ item }}</span>
          </li>
        </ul>

        <ul class="space-y-3" aria-label="Course includes right column">
          <li v-for="item in right" :key="item" class="flex items-start gap-3 text-slate-700">
            <span aria-hidden="true">▸</span>
            <span class="text-sm">{{ item }}</span>
          </li>
        </ul>
      </div>
    </div>
  </Section>
</template>
