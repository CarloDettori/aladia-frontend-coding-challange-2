<script setup lang="ts">
import { ref } from 'vue'
import Section from '~/components/common/Section.vue'
import SectionTitle from '~/components/common/SectionTitle.vue'

type Instructor = {
  name: string
  role: string
  rating: string
  reviews: string
  students: string
  courses: string
  bio: string
}

const instructors = ref<Instructor[]>([
  {
    name: 'Dr. Angela Yu',
    role: 'Developer and Lead Instructor',
    rating: '4,7',
    reviews: '414.294',
    students: '1.745.088',
    courses: '7',
    bio: 'Angela is a developer with a passion for teaching. She has taught millions of students how to code and enjoys breaking down complex topics into practical, project-based lessons. In this course you’ll build real apps, games, and automation scripts while learning professional Python workflows.'
  }
])

const expanded = ref<Record<string, boolean>>({})
const toggleBio = (name: string) => {
  expanded.value[name] = !expanded.value[name]
}
</script>

<template>
  <Section>
    <div>
      <SectionTitle title="Istruttore" />

      <div class="space-y-8">
        <article
          v-for="inst in instructors"
          :key="inst.name"
          class="rounded-xl border border-slate-200 bg-white p-6 shadow-sm"
        >
          <!-- Header -->
          <header
            class="flex flex-col gap-4 sm:flex-row sm:items-start sm:justify-between"
          >
            <div class="min-w-0">
              <h3 class="text-xl font-extrabold text-slate-900">
                <a href="#" class="hover:underline">{{ inst.name }}</a>
              </h3>
              <p class="mt-1 text-sm text-slate-600">{{ inst.role }}</p>

              <!-- Stats row -->
              <dl
                class="mt-4 grid grid-cols-2 gap-3 text-sm sm:flex sm:flex-wrap sm:gap-x-6 sm:gap-y-2"
              >
                <div class="flex items-center gap-2">
                  <dt class="sr-only">Rating</dt>
                  <dd class="text-slate-700">
                    <span aria-hidden="true">⭐</span>
                    <span class="ml-1 font-semibold">{{ inst.rating }}</span>
                    <span class="ml-1 text-slate-500"
                      >valutazione istruttore</span
                    >
                  </dd>
                </div>

                <div class="flex items-center gap-2">
                  <dt class="sr-only">Reviews</dt>
                  <dd class="text-slate-700">
                    <span aria-hidden="true">💬</span>
                    <span class="ml-1 font-semibold">{{ inst.reviews }}</span>
                    <span class="ml-1 text-slate-500">recensioni</span>
                  </dd>
                </div>

                <div class="flex items-center gap-2">
                  <dt class="sr-only">Students</dt>
                  <dd class="text-slate-700">
                    <span aria-hidden="true">👥</span>
                    <span class="ml-1 font-semibold">{{ inst.students }}</span>
                    <span class="ml-1 text-slate-500">studenti</span>
                  </dd>
                </div>

                <div class="flex items-center gap-2">
                  <dt class="sr-only">Courses</dt>
                  <dd class="text-slate-700">
                    <span aria-hidden="true">▶</span>
                    <span class="ml-1 font-semibold">{{ inst.courses }}</span>
                    <span class="ml-1 text-slate-500">corsi</span>
                  </dd>
                </div>
              </dl>
            </div>

            <!-- Avatar -->
            <div class="flex shrink-0 items-start gap-4">
              <div
                class="grid size-20 place-items-center rounded-full bg-slate-200 text-2xl font-extrabold text-slate-700"
                aria-hidden="true"
              >
                AU
              </div>
            </div>
          </header>

          <!-- Bio -->
          <div class="mt-5 text-sm leading-relaxed text-slate-700">
            <p :class="expanded[inst.name] ? '' : 'line-clamp-4'">
              {{ inst.bio }}
            </p>

            <button
              type="button"
              class="mt-3 inline-flex items-center gap-2 text-sm font-semibold text-violet-700 hover:underline"
              @click="toggleBio(inst.name)"
              :aria-expanded="!!expanded[inst.name]"
              :aria-controls="`bio-${inst.name.replaceAll(' ', '-')}`"
            >
              <span>{{
                expanded[inst.name] ? 'Mostra meno' : 'Mostra di più'
              }}</span>
              <span aria-hidden="true">{{
                expanded[inst.name] ? '▴' : '▾'
              }}</span>
            </button>

            <!-- hidden region for aria-controls target -->
            <span class="sr-only" :id="`bio-${inst.name.replaceAll(' ', '-')}`"
              >Bio</span
            >
          </div>
        </article>
      </div>
    </div>
  </Section>
</template>
