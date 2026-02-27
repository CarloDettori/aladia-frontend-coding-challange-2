<script setup lang="ts">
import PageLayout from '~/layouts/PageLayout.vue'
import Hero from '~/components/udemy/Hero.vue'
import CTAVideo from '~/components/udemy/CTAVideo.vue'
import CTAPanel from '~/components/udemy/CTAPanel.vue'
import CTAAside from '~/components/udemy/CTAAside.vue'

import WhatYouLearn from '~/components/udemy/WhatYouLearn.vue'
import Includes from '~/components/udemy/Includes.vue'
import CurriculumPreview from '~/components/udemy/CurriculumPreview.vue'
import Description from '~/components/udemy/Description.vue'
import Instructors from '~/components/udemy/Instructors.vue'
import Reviews from '~/components/udemy/Reviews.vue'
import FAQ from '~/components/udemy/FAQ.vue'
import RelatedTopics from '~/components/udemy/RelatedTopics.vue'
import CodingExercises from '~/components/udemy/CodingExercises.vue'
import Requirements from '~/components/udemy/Requirements.vue'
import StudentsAlsoBought from '~/components/udemy/StudentsAlsoBought.vue'
import WhoThisCourseIsFor from '~/components/udemy/WhoThisCourseIsFor.vue'
import MoreCoursesByInstructor from '~/components/udemy/MoreCoursesByInstructor.vue'
import AiProgrammer from '~/components/udemy/AiProgrammer.vue'
AiProgrammer
</script>

<template>
  <PageLayout :hero-bg-enabled="true" hero-bg-height="560px">
    <template #main>
      <!-- DESKTOP (>= xl): hero dark -->
      <div class="hidden xl:block">
        <Hero variant="dark" />
      </div>

      <!-- MOBILE/TABLET (< xl): video -> hero light -> panel -->
      <div class="xl:hidden space-y-6 py-6">
        <CTAVideo />
        <Hero variant="light" />
        <CTAPanel />
      </div>

      <!-- Rest of page -->
      <div class="bg-white">
        <WhatYouLearn class="mt-8" />
  <RelatedTopics class="mt-8" />
  <Includes class="mt-8" />
  <CodingExercises class="mt-10" />
  <CurriculumPreview class="mt-10" />
  <Requirements class="mt-10" />
  <Description class="mt-10" />
  <WhoThisCourseIsFor class="mt-10" />
  <StudentsAlsoBought class="mt-10" />
  <AiProgrammer class="mt-10" />
  <MoreCoursesByInstructor class="mt-10" />
  <Instructors class="mt-10" />
  <Reviews class="mt-10" />
  <FAQ class="mt-10" />

      </div>
    </template>

    <template #aside>
      <!-- DESKTOP (>= xl): sticky CTA -->
      <div class="hidden xl:block pt-8 xl:-mt-40">
        <CTAAside />
      </div>
    </template>
  </PageLayout>
</template>
