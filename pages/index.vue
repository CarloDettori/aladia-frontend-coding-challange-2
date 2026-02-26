<script setup lang="ts">
import PageLayout from '~/layouts/PageLayout.vue';
import Hero from '~/components/udemy/Hero.vue';
import WhatYouLearn from '~/components/udemy/WhatYouLearn.vue';
import Includes from '~/components/udemy/Includes.vue';
import CurriculumPreview from '~/components/udemy/CurriculumPreview.vue';
import Description from '~/components/udemy/Description.vue';
import Instructors from '~/components/udemy/Instructors.vue';
import Reviews from '~/components/udemy/Reviews.vue';
import FAQ from '~/components/udemy/FAQ.vue';
import CTAAside from '~/components/udemy/CTAAside.vue';
</script>


<template>
  <PageLayout>

    <template #main>

      <Hero />

      <div class="bg-white">
        <WhatYouLearn class="mt-8" />
        <Includes class="mt-8" />
        <CurriculumPreview class="mt-10" />
        <Description class="mt-10" />
        <Instructors class="mt-10" />
        <Reviews class="mt-10" />
        <FAQ class="mt-10" />
      </div>

    </template>

    <template #aside>

      <div class="pt-8 lg:-mt-40"">
      <CTAAside />
      </div>

    </template>

  </PageLayout>
</template>
