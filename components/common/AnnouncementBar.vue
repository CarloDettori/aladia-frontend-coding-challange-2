<script setup lang="ts">
import { ref } from 'vue'

const isClosed = ref(false)

const message =
  'Termina tra 8 h 57 min 4 sec. Gli sconti terminano oggi'
const secondary =
  'Preparati al futuro con le competenze giuste, a partire da 12,99 €.'
</script>

<template>
  <div
    v-if="!isClosed"
    class="relative bg-teal-200 text-slate-900 z-50"
    role="region"
    aria-label="Promotional announcement"
  >
    <div class="mx-auto w-full max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-center gap-3 py-2 text-sm">
        <p class="text-center">
          <strong>{{ message }}</strong>
          <span class="mx-2">|</span>
          <span>{{ secondary }}</span>
        </p>

        <button
          type="button"
          class="ml-auto inline-flex h-8 w-8 items-center justify-center rounded hover:bg-black/10"
          aria-label="Close announcement"
          @click="isClosed = true"
        >
          ✕
        </button>
      </div>
    </div>
  </div>
</template>