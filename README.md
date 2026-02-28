# Complex Layout Clone -- Udemy Course Page (Nuxt 3)

Rebuild of a complex, content-heavy course page inspired by Udemy using
**Nuxt 3** and **Tailwind CSS**.

The goal of this assessment is to demonstrate:

-   Clear and scalable component architecture
-   Clean, maintainable Nuxt codebase
-   Responsive layout handling
-   Accessibility awareness
-   Basic SEO awareness
-   Consistent code style (ESLint + Prettier)

------------------------------------------------------------------------

## Tech Stack

-   **Nuxt 3**
-   **Vue 3** (Composition API + `<script setup>`)
-   **TypeScript**
-   **Tailwind CSS**
-   **ESLint**
-   **Prettier**

------------------------------------------------------------------------

## Setup

Install dependencies:

``` bash
npm install
```

Run locally:

``` bash
npm run dev
```

Build:

``` bash
npm run build
npm run preview
```

Lint:

``` bash
npm run lint
```

Fix lint issues:

``` bash
npm run lint:fix
```

Format:

``` bash
npm run format
```

------------------------------------------------------------------------

## Live Preview

-   Live URL: TODO
-   Video walkthrough: TODO

------------------------------------------------------------------------

## Project Structure

    components/
      common/
        Container.vue
        Section.vue
        SectionTitle.vue
        Badge.vue
        RatingStars.vue
        AnnouncementBar.vue
      udemy/
        Hero.vue
        StickyCourseBar.vue
        CTAAside.vue
        CTAVideo.vue
        CTAPanel.vue
        WhatYouLearn.vue
        RelatedTopics.vue
        Includes.vue
        CodingExercises.vue
        CurriculumPreview.vue
        Requirements.vue
        WhoThisCourseIsFor.vue
        StudentsAlsoBought.vue
        AiProgrammer.vue
        MoreCoursesByInstructor.vue
        Instructors.vue
        Reviews.vue
        FAQ.vue

    layouts/
      PageLayout.vue
      Header.vue
      Footer.vue

    pages/
      index.vue

------------------------------------------------------------------------

## Architecture & Approach

### 1) Layout-first architecture

The page is built around a `PageLayout.vue` layout component that
defines:

-   Main / Aside structure (2 columns on desktop)
-   Sticky behavior for the CTA on large screens
-   Header / announcement area and global page skeleton
-   Slots to keep page composition clean (`#main`, `#aside`)

------------------------------------------------------------------------

### 2) Component-per-section strategy

Because the target page is content-heavy, each major section is isolated
into a dedicated component:

-   Improves readability and maintainability
-   Avoids a single monolithic page file
-   Makes sections easy to iterate on and reorder
-   Encourages reusability

------------------------------------------------------------------------

### 3) Shared UI building blocks

Common layout patterns and small UI primitives are extracted:

-   `Container.vue` / `Section.vue` for spacing
-   `Badge.vue` for labels
-   `RatingStars.vue` for ratings
-   `SectionTitle.vue` for consistent headings

------------------------------------------------------------------------

## Responsiveness

Mobile-first approach with Tailwind breakpoints.

Desktop (`>= xl / 1280px`): - Two-column layout - Sticky CTA - Dark hero
variant - Video hides on scroll (desktop enhancement)

Mobile (`< xl`): - Linear stacked layout - CTA flows naturally in page -
Light hero variant

------------------------------------------------------------------------

## Accessibility

-   Semantic HTML structure
-   ARIA attributes where needed
-   Proper button types
-   Keyboard-friendly components

------------------------------------------------------------------------

## SEO Awareness

-   Clear heading hierarchy
-   Semantic structure
-   Clean markup
-   Image alt attributes

------------------------------------------------------------------------

## Code Style

-   ESLint for linting
-   Prettier for formatting

Scripts: - `npm run lint` - `npm run lint:fix` - `npm run format`

------------------------------------------------------------------------

## What I Would Improve With More Time

-   Add unit tests
-   Improve image optimization
-   Extract static content into mock JSON files
-   Add Open Graph / structured metadata
-   Add i18n support
-   Refine micro-interactions

------------------------------------------------------------------------

## Video Walkthrough Outline

1.  Intro & challenge overview
2.  Project structure
3.  Layout logic
4.  Responsive behavior
5.  Component architecture
6.  Accessibility
7.  Code quality
8.  Possible improvements

------------------------------------------------------------------------

## Notes

Pixel-perfect replication is not required; focus is on:

-   Visual similarity
-   Clean architecture
-   Maintainability
-   Scalable structure
