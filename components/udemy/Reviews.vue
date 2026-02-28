<script setup lang="ts">
import Section from '~/components/common/Section.vue'
import SectionTitle from '~/components/common/SectionTitle.vue'
import RatingStars from '~/components/common/RatingStars.vue'

type Review = {
  name: string
  initials: string
  rating: number
  date: string
  text: string
}

const summary = {
  rating: 4.7,
  count: '414.294'
}

const reviews: Review[] = [
  {
    name: 'Marco R.',
    initials: 'MR',
    rating: 5,
    date: '1 settimana fa',
    text: 'Corso super completo e ben strutturato. Mi ha aiutato a costruire una routine giornaliera e a consolidare Python con progetti reali.'
  },
  {
    name: 'Giulia S.',
    initials: 'GS',
    rating: 5,
    date: '2 settimane fa',
    text: 'Spiegazioni chiare e progressione ottima. I mini-progetti sono il punto forte: ti fanno capire davvero cosa stai facendo.'
  },
  {
    name: 'Luca B.',
    initials: 'LB',
    rating: 4,
    date: '3 settimane fa',
    text: 'Tantissimo contenuto, a volte intenso, ma la qualità è alta. Consigliato a chi vuole fare un salto di livello con Python.'
  },
  {
    name: 'Sara P.',
    initials: 'SP',
    rating: 5,
    date: '1 mese fa',
    text: 'Ho apprezzato il focus pratico: automazione, web, data. È uno di quei corsi che puoi mettere in portfolio.'
  }
]
</script>

<template>
  <Section>
    <div>
      <SectionTitle title="Valutazioni e recensioni" />

      <!-- Summary -->
      <div
        class="mt-4 flex flex-col gap-4 sm:flex-row sm:items-center sm:gap-8"
      >
        <div class="flex items-center gap-4">
          <div class="text-5xl font-extrabold text-slate-900">
            {{ summary.rating }}
          </div>
          <div>
            <RatingStars :value="summary.rating" />
            <div class="mt-1 text-sm text-slate-600">
              {{ summary.count }} valutazioni
            </div>
          </div>
        </div>

        <p class="text-sm text-slate-600">
          Le recensioni più recenti (esempio statico) per mostrare la struttura
          della sezione.
        </p>
      </div>

      <!-- Reviews grid -->
      <div class="mt-6 grid gap-6 lg:grid-cols-2">
        <article
          v-for="r in reviews"
          :key="r.name + r.date"
          class="rounded-xl border border-slate-200 bg-white p-6 shadow-sm"
        >
          <header class="flex items-start justify-between gap-4">
            <div class="flex items-start gap-4">
              <div
                class="grid size-12 place-items-center rounded-full bg-slate-200 text-sm font-extrabold text-slate-700"
                aria-hidden="true"
              >
                {{ r.initials }}
              </div>

              <div class="min-w-0">
                <h3 class="truncate font-semibold text-slate-900">
                  {{ r.name }}
                </h3>
                <div
                  class="mt-1 flex flex-wrap items-center gap-2 text-sm text-slate-600"
                >
                  <RatingStars :value="r.rating" />
                  <span class="text-slate-400">•</span>
                  <span>{{ r.date }}</span>
                </div>
              </div>
            </div>

            <button
              type="button"
              class="shrink-0 text-slate-500 hover:text-slate-700"
              aria-label="More options"
            >
              ⋯
            </button>
          </header>

          <p class="mt-4 text-sm leading-relaxed text-slate-700">
            {{ r.text }}
          </p>

          <button
            type="button"
            class="mt-4 text-sm font-semibold text-violet-700 hover:underline"
          >
            Mostra di più
          </button>
        </article>
      </div>

      <button
        type="button"
        class="mt-8 rounded-lg border border-slate-900 px-4 py-3 text-sm font-bold text-slate-900 hover:bg-slate-50"
      >
        Mostra tutte le recensioni
      </button>
    </div>
  </Section>
</template>
