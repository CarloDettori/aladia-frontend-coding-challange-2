<script setup lang="ts">
import Header from './Header.vue';
import Footer from './Footer.vue';

</script>


<template>
  <Header/>
  <div class="w-full">
    <!-- Outer container -->
    <div class="mx-auto w-full max-w-7xl px-4 sm:px-6 lg:px-8">
      <!-- Grid -->
      <div class="grid grid-cols-1 gap-8 lg:grid-cols-12">
        <!-- Main content -->
        <main class="lg:col-span-8 xl:col-span-8">
          <slot name="main" />
        </main>

        <!-- Aside (CTA) -->
        <aside class="lg:col-span-4 xl:col-span-4">
          <!-- Sticky wrapper -->
          <div class="lg:sticky lg:top-6">
            <slot name="aside" />
          </div>
        </aside>
      </div>
    </div>
  </div>
  <Footer/>
</template>
