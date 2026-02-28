<script setup lang="ts">
import Section from '~/components/common/Section.vue'
import SectionTitle from '~/components/common/SectionTitle.vue'

const items = [
  'Principianti assoluti che vogliono imparare Python partendo da zero.',
  'Chi vuole costruire un portfolio con progetti reali e completi.',
  'Sviluppatori che vogliono usare Python per automazione, web e data.',
  'Studenti che vogliono una roadmap strutturata e pratica.'
]
</script>

<template>
  <Section>
    <div>
      <SectionTitle title="A chi è rivolto questo corso" />

      <ul
        class="mt-4 list-disc space-y-2 pl-5 text-sm text-slate-700"
        aria-label="Target audience"
      >
        <li v-for="i in items" :key="i">
          {{ i }}
        </li>
      </ul>
    </div>
  </Section>
</template>
