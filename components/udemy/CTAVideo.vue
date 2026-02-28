<script setup lang="ts"></script>

<template>
  <div class="overflow-hidden rounded-xl border bg-white shadow-lg">
    <div class="relative aspect-video bg-slate-200">
      <!-- placeholder video -->
      <button
        type="button"
        class="absolute inset-0 flex items-center justify-center"
        aria-label="Play course preview video"
      >
        <span
          class="grid size-14 place-items-center rounded-full bg-white/90 text-slate-900 shadow"
        >
          ▶
        </span>
      </button>

      <div
        class="absolute bottom-3 left-3 text-xs font-semibold text-white drop-shadow"
      >
        Visualizza in anteprima questo corso
      </div>
    </div>
  </div>
</template>
