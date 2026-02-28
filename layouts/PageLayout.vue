<script setup lang="ts">
import Header from './Header.vue'
import Footer from './Footer.vue'
import AnnouncementBar from '~/components/common/AnnouncementBar.vue'
import StickyCourseBar from '~/components/udemy/StickyCourseBar.vue'

const props = withDefaults(
  defineProps<{
    heroBgEnabled?: boolean
    heroBgHeight?: string
  }>(),
  { heroBgEnabled: false, heroBgHeight: '560px' }
)
</script>

<template>
  <!-- Barra sopra header -->
  <AnnouncementBar />

  <Header />

  <!-- Barra fixed dietro header -->
  <StickyCourseBar />

  <div class="w-full relative">
    <div
      v-if="props.heroBgEnabled"
      :style="{ height: props.heroBgHeight }"
      aria-hidden="true"
      class="absolute inset-x-0 top-0 xl:bg-[#020617]"
    />

    <div class="mx-auto w-full max-w-7xl px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="grid grid-cols-1 gap-8 xl:grid-cols-12">
        <main class="xl:col-span-8">
          <slot name="main" />
        </main>

        <aside class="xl:col-span-4">
          <div class="xl:sticky xl:top-24">
            <slot name="aside" />
          </div>
        </aside>
      </div>
    </div>
  </div>

  <Footer />
</template>
