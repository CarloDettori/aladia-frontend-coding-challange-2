<script setup lang="ts">
type MiniCourse = {
  id: string
  title: string
  subtitle: string
  instructor: string
  imageAlt: string
  imageSrc?: string
  isBestSeller?: boolean
  rating?: number
  ratingCountLabel?: string
}

const courses: MiniCourse[] = [
  {
    id: 'ai-programmer',
    title: 'Succeed in the Age of AI',
    subtitle: 'Learn Faster, Code Better, Achieve More',
    instructor: 'Dr. Angela Yu, Developer and Lead Instructor',
    imageAlt: 'Course thumbnail: Succeed in the Age of AI',
    // se vuoi metti path reali in /public/images/...
    imageSrc: '/images/ai-1.jpg',
    isBestSeller: true,
    rating: 4.6,
    ratingCountLabel: '2007 ratings'
  },
  {
    id: 'fullstack',
    title: 'The Complete Full-Stack Web Development Bootcamp',
    subtitle:
      'Become a Full-Stack Web Developer with just ONE course. HTML, CSS, JavaScript, Node, React, PostgreSQL, Web3 and DApps',
    instructor: 'Dr. Angela Yu, Developer and Lead Instructor',
    imageAlt: 'Course thumbnail: Full-Stack Web Development Bootcamp',
    imageSrc: '/images/ai-2.jpg',
    isBestSeller: true,
    rating: 4.7,
    ratingCountLabel: '465.382 ratings'
  },
  {
    id: '100-days',
    title: '100 Days of Code™: The Complete Python Pro Bootcamp',
    subtitle:
      'Master Python by building 100 projects in 100 days. Learn data science, automation, build websites, games and apps!',
    instructor: 'Dr. Angela Yu, Developer and Lead Instructor',
    imageAlt: 'Course thumbnail: 100 Days of Code Python',
    imageSrc: '/images/ai-3.jpg',
    isBestSeller: true,
    rating: 4.7,
    ratingCountLabel: '414.431 ratings'
  }
]

const totalLabel = 'Totale: 51,97 €'
const oldTotalLabel = '69,97 €'
</script>

<template>
  <section aria-labelledby="ai-programmer-title" class="mt-10">
    <CommonSection>
      <div class="space-y-6">
        <h2
          id="ai-programmer-title"
          class="text-3xl font-extrabold tracking-tight text-slate-900"
        >
          The AI Programmer
        </h2>

        <div class="space-y-5">
          <template v-for="(c, idx) in courses" :key="c.id">
            <article
              class="relative overflow-hidden rounded-2xl border border-slate-200 bg-white shadow-sm"
              aria-label="Related course card"
            >
              <div class="flex flex-col gap-4 p-4 sm:flex-row sm:items-center">
                <!-- Thumb -->
                <div class="w-full sm:w-52">
                  <div
                    class="aspect-[16/9] w-full overflow-hidden rounded-xl bg-slate-100 ring-1 ring-slate-200"
                  >
                    <img
                      v-if="c.imageSrc"
                      :src="c.imageSrc"
                      :alt="c.imageAlt"
                      class="h-full w-full object-cover"
                      loading="lazy"
                    />
                    <div
                      v-else
                      class="flex h-full w-full items-center justify-center text-slate-400"
                    >
                      (image)
                    </div>
                  </div>
                </div>

                <!-- Text -->
                <div class="flex-1">
                  <div class="flex flex-col gap-1">
                    <h3
                      class="text-base font-extrabold text-slate-900 sm:text-lg"
                    >
                      {{ c.title }}
                    </h3>
                    <p class="text-sm text-slate-700">
                      {{ c.subtitle }}
                    </p>
                    <p class="text-xs text-slate-500">
                      {{ c.instructor }}
                    </p>
                  </div>

                  <!-- Meta row -->
                  <div class="mt-3 flex flex-wrap items-center gap-2">
                    <CommonBadge v-if="c.isBestSeller" variant="success"
                      >Best seller</CommonBadge
                    >

                    <span
                      v-if="typeof c.rating === 'number'"
                      class="inline-flex items-center gap-2 rounded-md border border-slate-200 bg-white px-2 py-1 text-xs font-semibold text-slate-700"
                      aria-label="Course rating"
                    >
                      <span aria-hidden="true">★</span>
                      <span>{{ c.rating.toFixed(1) }}</span>
                    </span>

                    <span
                      v-if="c.ratingCountLabel"
                      class="inline-flex items-center rounded-md border border-slate-200 bg-white px-2 py-1 text-xs text-slate-600"
                    >
                      {{ c.ratingCountLabel }}
                    </span>
                  </div>
                </div>
              </div>

              <!-- (Optional) clickable overlay -->
              <a href="#" class="absolute inset-0" aria-label="Open course" />
            </article>

            <!-- Plus separator (between cards) -->
            <div
              v-if="idx < courses.length - 1"
              class="relative flex items-center justify-center py-2"
              aria-hidden="true"
            >
              <div
                class="absolute left-0 right-0 top-1/2 h-px -translate-y-1/2 bg-slate-200"
              />
              <div
                class="relative grid h-10 w-10 place-items-center rounded-full border border-slate-200 bg-white"
              >
                <span class="text-xl leading-none text-slate-600">+</span>
              </div>
            </div>
          </template>

          <!-- Totals row -->
          <div class="flex flex-wrap items-center justify-end gap-3 pt-2">
            <div class="text-sm text-slate-700">
              <span class="font-semibold">{{ totalLabel }}</span>
              <span class="ml-2 text-slate-400 line-through">{{
                oldTotalLabel
              }}</span>
            </div>

            <button
              type="button"
              class="rounded-lg bg-violet-700 px-4 py-2 text-sm font-bold text-white hover:bg-violet-800 focus:outline-none focus:ring-2 focus:ring-violet-500"
              aria-label="Add all to cart"
            >
              Aggiungi tutto al carrello
            </button>
          </div>
        </div>
      </div>
    </CommonSection>
  </section>
</template>
