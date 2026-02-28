<script setup lang="ts">
import { ref } from 'vue'

const active = ref<'personal' | 'team'>('personal')
</script>

<template>
  <div class="rounded-xl border bg-white shadow-lg">
    <!-- Tabs header -->
    <div class="grid grid-cols-2 border-b">
      <button
        type="button"
        class="px-4 py-3 text-sm font-semibold"
        :class="
          active === 'personal'
            ? 'border-b-2 border-slate-900'
            : 'text-slate-500'
        "
        @click="active = 'personal'"
        aria-controls="panel-personal"
        :aria-selected="active === 'personal'"
        role="tab"
      >
        Per uso personale
      </button>

      <button
        type="button"
        class="px-4 py-3 text-sm font-semibold"
        :class="
          active === 'team' ? 'border-b-2 border-slate-900' : 'text-slate-500'
        "
        @click="active = 'team'"
        aria-controls="panel-team"
        :aria-selected="active === 'team'"
        role="tab"
      >
        Per uso in team
      </button>
    </div>

    <!-- Panel -->
    <div class="p-5">
      <div v-show="active === 'personal'" id="panel-personal" role="tabpanel">
        <p class="text-xs text-slate-500">
          Questo corso premium è incluso nei piani
        </p>
        <h3 class="mt-2 text-xl font-extrabold text-slate-900">
          Abbonati ai migliori corsi di Udemy
        </h3>
        <p class="mt-2 text-sm text-slate-600">
          Accedi a questo corso e a oltre 26.850 dei nostri corsi più votati con
          Piano individuale.
        </p>

        <a
          href="#"
          class="mt-2 inline-block text-sm font-semibold text-violet-700 hover:underline"
          >Scopri di più</a
        >

        <button
          type="button"
          class="mt-4 w-full rounded-lg bg-violet-700 px-4 py-3 text-sm font-bold text-white hover:bg-violet-800"
        >
          Abbonati
        </button>

        <div class="mt-4 border-t pt-4">
          <div class="flex items-baseline gap-2">
            <span class="text-2xl font-extrabold text-slate-900">16,99 €</span>
            <span class="text-sm text-slate-500 line-through">19,99 €</span>
            <span class="text-sm text-slate-600">15% di sconto</span>
          </div>
          <p class="mt-1 text-sm text-red-600">
            ⏱ Solo 11 ore a questo prezzo!
          </p>

          <button
            type="button"
            class="mt-4 w-full rounded-lg border border-violet-700 px-4 py-3 text-sm font-bold text-violet-700 hover:bg-violet-50"
          >
            Aggiungi al carrello
          </button>

          <button
            type="button"
            class="mt-3 w-full rounded-lg border border-violet-700 px-4 py-3 text-sm font-bold text-violet-700 hover:bg-violet-50"
          >
            Acquista ora
          </button>
        </div>
      </div>

      <div v-show="active === 'team'" id="panel-team" role="tabpanel">
        <h3 class="text-xl font-extrabold text-slate-900">Udemy Business</h3>
        <p class="mt-2 text-sm text-slate-600">
          Forma il tuo team con una libreria di corsi per aziende.
        </p>
        <button
          type="button"
          class="mt-4 w-full rounded-lg bg-slate-900 px-4 py-3 text-sm font-bold text-white hover:bg-slate-800"
        >
          Contatta il team vendite
        </button>
      </div>
    </div>
  </div>
</template>
