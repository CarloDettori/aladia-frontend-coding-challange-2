<script setup lang="ts">
import Section from '~/components/common/Section.vue'
import SectionTitle from '~/components/common/SectionTitle.vue'
</script>

<template>
  <Section>
    <div class="rounded-xl border border-slate-200 bg-white p-6 shadow-sm">
      <div
        class="flex flex-col gap-6 md:flex-row md:items-center md:justify-between"
      >
        <div class="min-w-0">
          <SectionTitle title="Esercizi di codifica" />
          <p class="mt-2 text-sm text-slate-700">
            Metti in pratica ciò che impari con esercizi guidati e feedback
            immediato. (Sezione statica per la challenge)
          </p>

          <div class="mt-4 flex flex-wrap gap-3">
            <a
              href="#"
              class="inline-flex items-center justify-center rounded-lg bg-slate-900 px-4 py-2 text-sm font-bold text-white hover:bg-slate-800"
            >
              Guarda una demo
            </a>

            <a
              href="#"
              class="inline-flex items-center justify-center rounded-lg border border-slate-300 px-4 py-2 text-sm font-bold text-slate-900 hover:bg-slate-50"
            >
              Scopri di più
            </a>
          </div>
        </div>

        <!-- Placeholder image -->
        <div
          class="h-32 w-full shrink-0 overflow-hidden rounded-lg bg-slate-100 md:h-40 md:w-64"
          aria-hidden="true"
        >
          <div class="grid h-full w-full place-items-center text-slate-400">
            preview
          </div>
        </div>
      </div>
    </div>
  </Section>
</template>
