<script setup lang="ts">
import { ref } from 'vue'
import Section from '~/components/common/Section.vue'
import SectionTitle from '~/components/common/SectionTitle.vue'

type FAQItem = {
  q: string
  a: string
}

const faqs: FAQItem[] = [
  {
    q: 'Quando posso iniziare il corso?',
    a: 'Subito. Il corso è disponibile on-demand e puoi iniziare quando vuoi, seguendo le lezioni al tuo ritmo.'
  },
  {
    q: 'Ho bisogno di esperienza precedente in programmazione?',
    a: 'No. Il corso parte dalle basi e cresce progressivamente con esercizi e progetti. È adatto anche a principianti.'
  },
  {
    q: 'Il corso include un certificato?',
    a: 'Sì. Al completamento del corso riceverai un certificato di completamento (come previsto dalla piattaforma).'
  },
  {
    q: 'Posso accedere ai contenuti da mobile?',
    a: 'Sì. Puoi seguire il corso da desktop, mobile o TV tramite le app disponibili.'
  }
]

const openIndex = ref<number>(0)

const toggle = (index: number) => {
  openIndex.value = openIndex.value === index ? -1 : index
}
</script>

<template>
  <Section>
    <div>
      <SectionTitle title="Domande frequenti" />

      <div class="mt-4 overflow-hidden rounded-xl border border-slate-200 bg-white">
        <div
          v-for="(item, index) in faqs"
          :key="item.q"
          class="border-b border-slate-200 last:border-b-0"
        >
          <h3>
            <button
              type="button"
              class="flex w-full items-center justify-between gap-4 px-5 py-4 text-left hover:bg-slate-50"
              :aria-expanded="openIndex === index"
              :aria-controls="`faq-panel-${index}`"
              @click="toggle(index)"
            >
              <span class="font-semibold text-slate-900">{{ item.q }}</span>
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
            :id="`faq-panel-${index}`"
            v-show="openIndex === index"
            class="px-5 pb-4 text-sm leading-relaxed text-slate-700"
          >
            {{ item.a }}
          </div>
        </div>
      </div>
    </div>
  </Section>
</template>
