<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue'

const isMenuOpen = ref(false)

const mainLinks = [
  { label: 'Accedi', href: '#' },
  { label: 'Registrati', href: '#' },
  { label: 'Abbonati', href: '#' }
]

const exploreLinks = [
  { label: "Sviluppa competenze sull'AI", href: '#' },
  { label: 'Lancia un nuovo profilo professionale', href: '#' },
  { label: 'Preparati per una certificazione', href: '#' },
  { label: 'Fai pratica con il Gioco di ruolo', href: '#' }
]

const popularLinks = [
  { label: 'Web Development', href: '#' },
  { label: 'IT Certification', href: '#' },
  { label: 'Data & Analytics', href: '#' },
  { label: 'Game Development', href: '#' },
  { label: 'Mobile Apps', href: '#' },
  { label: 'Finance', href: '#' },
  { label: 'Graphic Design', href: '#' },
  { label: 'Personal Transformation', href: '#' },
  { label: 'Entrepreneurship', href: '#' },
  { label: 'Digital Marketing', href: '#' }
]

const serviceLinks = [
  { label: 'Udemy Business', href: '#' },
  { label: "Scarica l'app", href: '#' }
]

const supportLinks = [
  { label: 'Invita gli amici', href: '#' },
  { label: 'Assistenza e supporto', href: '#' }
]

const closeMenu = () => (isMenuOpen.value = false)
const openMenu = () => (isMenuOpen.value = true)

const onKeyDown = (e: KeyboardEvent) => {
  if (e.key === 'Escape') closeMenu()
}



onMounted(() => window.addEventListener('keydown', onKeyDown))
onBeforeUnmount(() => window.removeEventListener('keydown', onKeyDown))
</script>

<template>
  <header class="relative z-50 border-b bg-white">
    <div class="mx-auto w-full max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="flex h-16 items-center justify-between gap-3">
        <!-- LEFT: hamburger (mobile) -->
        <button
          type="button"
          class="inline-flex items-center justify-center rounded-md p-2 text-slate-700 hover:bg-slate-100 md:hidden"
          aria-label="Open menu"
          :aria-expanded="isMenuOpen"
          aria-controls="mobile-drawer"
          @click="openMenu"
        >
          ☰
        </button>

        <!-- logo -->
        <a
          href="#"
          class=" xl:hidden text-xl font-extrabold tracking-tight text-slate-900"
          aria-label="Udemy home"
        >
          udemy
        </a>

        <!-- RIGHT: icons (mobile) -->
        <div class="flex items-center gap-2 md:hidden">
          <button class="rounded-md p-2 hover:bg-slate-100" type="button" aria-label="Search">
            🔍
          </button>
          <button class="rounded-md p-2 hover:bg-slate-100" type="button" aria-label="Cart">
            🛒
          </button>
        </div>

        <!-- DESKTOP HEADER (>= md) -->
        <div class="hidden w-full md:flex md:items-center md:gap-4">
          
          <a class="shrink-0 text-sm font-semibold text-slate-700 hover:text-slate-900" href="#">
            Esplora
          </a>

          <!-- Search -->
          <div class="flex flex-1 items-center">
            <label class="sr-only" for="search">Cerca corsi</label>
            <div class="relative w-full max-w-2xl">
              <span class="pointer-events-none absolute left-3 top-1/2 -translate-y-1/2 text-slate-500" aria-hidden="true">🔎</span>
              <input
                id="search"
                type="search"
                placeholder="Cerca..."
                class="w-full rounded-full border border-slate-300 bg-white py-2 pl-10 pr-4 text-sm outline-none transition focus:border-violet-500 focus:ring-2 focus:ring-violet-500"
              />
            </div>
          </div>

          <!-- Right links -->
          <nav class="hidden lg:flex items-center gap-4" aria-label="Header navigation">
            <a href="#" class="text-sm text-slate-700 hover:text-slate-900">Udemy Business</a>
            <a href="#" class="text-sm text-slate-700 hover:text-slate-900">Insegna su Udemy</a>
          </nav>

          <button class="hidden sm:inline-flex rounded-md p-2 text-slate-700 hover:bg-slate-100" type="button" aria-label="Cart">
            🛒
          </button>

          <div class="flex shrink-0 items-center gap-2">
            <button class="rounded-md border border-violet-700 px-3 py-2 text-sm font-bold text-violet-700 hover:bg-violet-50">
              Accedi
            </button>
            <button class="rounded-md bg-violet-700 px-3 py-2 text-sm font-bold text-white hover:bg-violet-800">
              Registrati
            </button>
            <button class="hidden sm:inline-flex rounded-md border border-slate-300 px-3 py-2 hover:bg-slate-50" type="button" aria-label="Language">
              🌐
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Mobile drawer + overlay -->
    <transition name="fade">
      <div
        v-if="isMenuOpen"
        class="fixed inset-0 z-50 bg-black/40"
        aria-hidden="true"
        @click="closeMenu"
      />
    </transition>

    <transition name="slide">
      <aside
        v-if="isMenuOpen"
        id="mobile-drawer"
        class="fixed left-0 top-0 z-50 h-full w-[78%] max-w-xs overflow-y-auto bg-white shadow-xl"
        role="dialog"
        aria-modal="true"
        aria-label="Mobile navigation"
      >
        <div class="flex items-center justify-end p-3">
          <button
            type="button"
            class="inline-flex size-10 items-center justify-center rounded-full border border-slate-200 hover:bg-slate-50"
            aria-label="Close menu"
            @click="closeMenu"
          >
            ✕
          </button>
        </div>

        <nav class="px-5 pb-6 text-sm">
          <!-- auth -->
          <ul class="space-y-3 pb-4">
            <li v-for="l in mainLinks" :key="l.label">
              <a :href="l.href" class="block text-slate-800 hover:underline">{{ l.label }}</a>
            </li>
          </ul>

          <hr class="my-4 border-slate-200" />

          <!-- explore -->
          <div class="pb-2 font-semibold text-slate-800">Esplora per obiettivo</div>
          <ul class="space-y-3">
            <li v-for="l in exploreLinks" :key="l.label" class="flex items-center justify-between gap-3">
              <a :href="l.href" class="block text-slate-700 hover:underline">{{ l.label }}</a>
              <span aria-hidden="true" class="text-slate-400">›</span>
            </li>
          </ul>

          <hr class="my-4 border-slate-200" />

          <!-- popular -->
          <div class="pb-2 font-semibold text-slate-800">Più popolari</div>
          <ul class="space-y-3">
            <li v-for="l in popularLinks" :key="l.label" class="flex items-center justify-between gap-3">
              <a :href="l.href" class="block text-slate-700 hover:underline">{{ l.label }}</a>
              <span aria-hidden="true" class="text-slate-400">›</span>
            </li>
          </ul>

          <hr class="my-4 border-slate-200" />

          <!-- services -->
          <div class="pb-2 font-semibold text-slate-800">Altri servizi di Udemy</div>
          <ul class="space-y-3">
            <li v-for="l in serviceLinks" :key="l.label" class="flex items-center justify-between gap-3">
              <a :href="l.href" class="block text-slate-700 hover:underline">{{ l.label }}</a>
              <span aria-hidden="true" class="text-slate-400">›</span>
            </li>
          </ul>

          <hr class="my-4 border-slate-200" />

          <!-- support -->
          <ul class="space-y-3">
            <li v-for="l in supportLinks" :key="l.label">
              <a :href="l.href" class="block text-slate-700 hover:underline">{{ l.label }}</a>
            </li>
          </ul>

          <!-- language bottom -->
          <div class="mt-8 flex items-center justify-between">
            <span class="text-slate-700">Lingua</span>
            <button
              type="button"
              class="inline-flex items-center gap-2 rounded-md border border-violet-700 px-3 py-2 font-semibold text-violet-700"
              aria-label="Change language"
            >
              🌐 Italiano
            </button>
          </div>
        </nav>
      </aside>
    </transition>
  </header>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.15s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 0.2s ease;
}
.slide-enter-from,
.slide-leave-to {
  transform: translateX(-100%);
}
</style>