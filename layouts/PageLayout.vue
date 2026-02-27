<script setup lang="ts">
import Header from './Header.vue'
import Footer from './Footer.vue'

const props = withDefaults(
  defineProps<{
    heroBgEnabled?: boolean
    heroBgHeight?: string
  }>(),
  {
    heroBgEnabled: true,
    // regola questa altezza finché lo sfondo copre hero + parte CTA come Udemy
    heroBgHeight: '560px'
  }
)
</script>

<template>
  <Header />

  <!-- Page wrapper -->
  <div class="relative w-full">
    <!-- Full-width hero background strip -->
    <div
      v-if="props.heroBgEnabled"
      aria-hidden="true"
      class="absolute inset-x-0 top-0 hidden bg-slate-950 xl:block"
      :style="{ height: props.heroBgHeight }"
    />

    <!-- Content container (keeps grid aligned) -->
    <div class="relative mx-auto w-full max-w-7xl px-4 sm:px-6 xl:px-8">
      <div class="grid grid-cols-1 gap-8 xl:grid-cols-12">
        <main class="xl:col-span-8 xl:col-span-8">
          <slot name="main" />
        </main>

        <aside class="xl:col-span-4 xl:col-span-4">
          <div class="xl:sticky xl:top-6">
            <slot name="aside" />
          </div>
        </aside>
      </div>
    </div>
  </div>

  <Footer />
</template>
