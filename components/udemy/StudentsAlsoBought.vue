<script setup lang="ts">
import CommonSection from '~/components/common/Section.vue'
import CommonSectionTitle from '~/components/common/SectionTitle.vue'
import CommonRatingStars from '~/components/common/RatingStars.vue'

type CourseRow = {
  title: string
  author: string
  rating: number
  reviews: string
  hours: string
  lectures: string
  level: string
  price: string
  badge?: string
}

const courses: CourseRow[] = [
  {
    title: 'The Complete Python Bootcamp From Zero to Hero',
    author: 'Jose Portilla',
    rating: 4.6,
    reviews: '520.123',
    hours: '22 ore',
    lectures: '155 lezioni',
    level: 'Tutti i livelli',
    price: '14,99 €',
    badge: 'Best seller'
  },
  {
    title: 'Python for Data Science and Machine Learning Bootcamp',
    author: 'Jose Portilla',
    rating: 4.6,
    reviews: '140.221',
    hours: '25 ore',
    lectures: '165 lezioni',
    level: 'Intermedio',
    price: '13,99 €'
  },
  {
    title: 'Automate the Boring Stuff with Python Programming',
    author: 'Al Sweigart',
    rating: 4.7,
    reviews: '113.004',
    hours: '9 ore',
    lectures: '50 lezioni',
    level: 'Principiante',
    price: '12,99 €',
    badge: 'Valutazioni più alte'
  }
]
</script>

<template>
  <CommonSection>
    <div>
      <CommonSectionTitle title="Gli studenti hanno acquistato anche" />

      <div class="mt-4 overflow-hidden rounded-xl border border-slate-200 bg-white">
        <article
          v-for="c in courses"
          :key="c.title"
          class="flex flex-col gap-4 border-b border-slate-200 p-5 last:border-b-0 sm:flex-row sm:items-start sm:justify-between"
        >
          <!-- Left -->
          <div class="flex min-w-0 gap-4">
            <!-- thumbnail placeholder -->
            <div class="h-16 w-28 shrink-0 rounded bg-slate-200" aria-hidden="true" />

            <div class="min-w-0">
              <h3 class="truncate font-bold text-slate-900">
                <a href="#" class="hover:underline">{{ c.title }}</a>
              </h3>
              <p class="mt-1 text-xs text-slate-600">{{ c.author }}</p>

              <div class="mt-2 flex flex-wrap items-center gap-2 text-xs text-slate-600">
                <span class="font-semibold text-slate-900">{{ c.rating.toFixed(1) }}</span>
                <CommonRatingStars :value="c.rating" size="sm" />
                <span class="text-slate-400">•</span>
                <span>({{ c.reviews }})</span>

                <span class="hidden sm:inline text-slate-400">•</span>
                <span class="hidden sm:inline">{{ c.hours }}</span>
                <span class="hidden sm:inline text-slate-400">•</span>
                <span class="hidden sm:inline">{{ c.lectures }}</span>
                <span class="hidden sm:inline text-slate-400">•</span>
                <span class="hidden sm:inline">{{ c.level }}</span>
              </div>

              <div v-if="c.badge" class="mt-2 inline-flex rounded bg-amber-200 px-2 py-0.5 text-xs font-semibold text-slate-900">
                {{ c.badge }}
              </div>
            </div>
          </div>

          <!-- Right -->
          <div class="flex shrink-0 items-center justify-between gap-4 sm:flex-col sm:items-end">
            <span class="text-sm font-extrabold text-slate-900">{{ c.price }}</span>
            <button
              type="button"
              class="rounded-md border border-slate-900 px-3 py-2 text-sm font-bold text-slate-900 hover:bg-slate-50"
            >
              Aggiungi al carrello
            </button>
          </div>
        </article>
      </div>

      <button
        type="button"
        class="mt-6 rounded-lg border border-slate-900 px-4 py-3 text-sm font-bold text-slate-900 hover:bg-slate-50"
      >
        Mostra altri corsi
      </button>
    </div>
  </CommonSection>
</template>