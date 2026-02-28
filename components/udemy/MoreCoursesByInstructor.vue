<script setup lang="ts">
import CommonSection from '~/components/common/Section.vue'
import CommonSectionTitle from '~/components/common/SectionTitle.vue'
import CommonRatingStars from '~/components/common/RatingStars.vue'

type CourseCard = {
  title: string
  author: string
  rating: number
  reviews: string
  price: string
  badge?: string
}

const courses: CourseCard[] = [
  {
    title: 'The Complete Web Development Bootcamp',
    author: 'Dr. Angela Yu',
    rating: 4.7,
    reviews: '290.000',
    price: '16,99 €',
    badge: 'Best seller'
  },
  {
    title: 'iOS & Swift - The Complete iOS App Development Bootcamp',
    author: 'Dr. Angela Yu',
    rating: 4.8,
    reviews: '160.000',
    price: '14,99 €'
  },
  {
    title: 'Complete Flutter Development Bootcamp with Dart',
    author: 'Dr. Angela Yu',
    rating: 4.6,
    reviews: '120.000',
    price: '13,99 €'
  }
]
</script>

<template>
  <CommonSection>
    <div>
      <CommonSectionTitle title="Altri corsi di questo istruttore" />

      <div class="mt-4 grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
        <article
          v-for="c in courses"
          :key="c.title"
          class="rounded-xl border border-slate-200 bg-white p-4 shadow-sm hover:shadow transition"
        >
          <!-- thumbnail -->
          <div
            class="aspect-[16/9] w-full rounded-lg bg-slate-200"
            aria-hidden="true"
          ></div>

          <h3 class="mt-3 line-clamp-2 text-sm font-extrabold text-slate-900">
            <a href="#" class="hover:underline">{{ c.title }}</a>
          </h3>

          <p class="mt-1 text-xs text-slate-600">{{ c.author }}</p>

          <div
            class="mt-2 flex flex-wrap items-center gap-2 text-xs text-slate-600"
          >
            <span class="font-semibold text-slate-900">{{
              c.rating.toFixed(1)
            }}</span>
            <CommonRatingStars :value="c.rating" size="sm" />
            <span class="text-slate-400">•</span>
            <span>({{ c.reviews }})</span>
          </div>

          <div
            v-if="c.badge"
            class="mt-2 inline-flex rounded bg-amber-200 px-2 py-0.5 text-xs font-semibold text-slate-900"
          >
            {{ c.badge }}
          </div>

          <div class="mt-3 text-sm font-extrabold text-slate-900">
            {{ c.price }}
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
