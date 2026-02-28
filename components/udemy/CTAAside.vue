<script setup lang="ts">
import { onMounted, onBeforeUnmount, ref } from 'vue'
import CTAVideo from '~/components/udemy/CTAVideo.vue'
import CTAPanel from '~/components/udemy/CTAPanel.vue'

const showVideo = ref(true)

let cleanup: (() => void) | null = null

onMounted(() => {
  const mq = window.matchMedia('(min-width: 1280px)') // xl
  const threshold = 220 // dopo quanto scroll nascondere il video (aggiustalo a gusto)

  const update = () => {
    // Solo xl: hide video on scroll
    if (mq.matches) {
      showVideo.value = window.scrollY < threshold
    } else {
      // sotto xl: video sempre visibile (layout verticale)
      showVideo.value = true
    }
  }

  update()
  window.addEventListener('scroll', update, { passive: true })
  mq.addEventListener?.('change', update)

  cleanup = () => {
    window.removeEventListener('scroll', update)
    mq.removeEventListener?.('change', update)
  }
})

onBeforeUnmount(() => cleanup?.())
</script>

<template>
  <!-- sticky + max height per non sbordare -->
  <div
    class="rounded-2xl bg-white p-2 shadow-sm ring-1 ring-slate-200
           xl:sticky xl:top-6
           xl:max-h-[calc(100vh-1.5rem)]
           xl:overflow-hidden"
  >
    <!-- Video: sparisce on scroll solo xl -->
    <div v-if="showVideo" class="mb-2">
      <CTAVideo />
    </div>

    <!-- Panel: scroll interno così resta tutto visibile -->
    <div class="xl:overflow-auto xl:max-h-[calc(100vh-1.5rem-0.5rem)]">
      <CTAPanel />
    </div>
  </div>
</template>
