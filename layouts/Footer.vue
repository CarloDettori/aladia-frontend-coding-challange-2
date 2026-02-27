<script setup lang="ts">
type LinkItem = { label: string; href: string }
type FooterSection = { title: string; links: LinkItem[] }

const sections: FooterSection[] = [
  {
    title: 'Certificazioni per organismo emittente',
    links: [
      { label: 'Certificazioni AWS (Amazon Web Services)', href: '#' },
      { label: 'Certificazioni Six Sigma', href: '#' },
      { label: 'Certificazioni Microsoft', href: '#' },
      { label: 'Certificazioni Cisco', href: '#' },
      { label: 'Certificazioni Tableau', href: '#' },
      { label: 'Vedi tutte le certificazioni', href: '#' }
    ]
  },
  {
    title: 'Certificazioni per competenza',
    links: [
      { label: 'Certificazione in cybersecurity', href: '#' },
      { label: 'Certificazione Project Management', href: '#' },
      { label: 'Certificazione Cloud', href: '#' },
      { label: 'Certificazione Data Analytics', href: '#' },
      { label: 'Certificazione Gestione HR', href: '#' },
      { label: 'Vedi tutte le certificazioni', href: '#' }
    ]
  },
  {
    title: 'Sviluppo Web',
    links: [
      { label: 'Sviluppo Web', href: '#' },
      { label: 'JavaScript', href: '#' },
      { label: 'React JavaScript', href: '#' },
      { label: 'Angular', href: '#' },
      { label: 'Java', href: '#' }
    ]
  },
  {
    title: 'Certificazioni IT',
    links: [
      { label: 'Amazon AWS', href: '#' },
      { label: 'AWS Certified Cloud Practitioner', href: '#' },
      { label: 'AZ-900: Microsoft Azure Fundamentals', href: '#' },
      { label: 'AWS Certified Solutions Architect - Associate', href: '#' },
      { label: 'Kubernetes', href: '#' }
    ]
  },
  {
    title: 'Leadership',
    links: [
      { label: 'Leadership', href: '#' },
      { label: 'Competenze di gestione', href: '#' },
      { label: 'Project Management', href: '#' },
      { label: 'Produttività personale', href: '#' },
      { label: 'Intelligenza emotiva', href: '#' }
    ]
  },
  {
    title: 'Data science',
    links: [
      { label: 'Data science', href: '#' },
      { label: 'Python', href: '#' },
      { label: 'Apprendimento automatico', href: '#' },
      { label: 'ChatGPT', href: '#' },
      { label: 'Apprendimento approfondito', href: '#' }
    ]
  },
  {
    title: 'Comunicazione',
    links: [
      { label: 'Competenze di comunicazione', href: '#' },
      { label: 'Competenze di presentazione', href: '#' },
      { label: 'Oratoria', href: '#' },
      { label: 'Scrittura', href: '#' },
      { label: 'PowerPoint', href: '#' }
    ]
  },
  {
    title: 'Business analytics e intelligence',
    links: [
      { label: 'Microsoft Excel', href: '#' },
      { label: 'SQL', href: '#' },
      { label: 'Microsoft Power BI', href: '#' },
      { label: 'Analisi dei dati', href: '#' },
      { label: 'Business Analysis', href: '#' }
    ]
  }
]

const bottomColumns = [
  {
    title: 'Informazioni',
    links: [
      { label: 'Lavora con noi', href: '#' },
      { label: 'Contattaci', href: '#' },
      { label: 'Blog', href: '#' },
      { label: 'Investitori', href: '#' }
    ]
  },
  {
    title: 'Scopri Udemy',
    links: [
      { label: "Scarica l'app", href: '#' },
      { label: 'Insegna su Udemy', href: '#' },
      { label: 'Piani e tariffe', href: '#' },
      { label: 'Affiliato', href: '#' },
      { label: 'Assistenza e supporto', href: '#' }
    ]
  },
  {
    title: 'Udemy for Business',
    links: [{ label: 'Udemy Business', href: '#' }]
  },
  {
    title: 'Informazioni legali e accessibilità',
    links: [
      { label: 'Dichiarazione di accessibilità', href: '#' },
      { label: 'Politica sulla privacy', href: '#' },
      { label: 'Mappa del sito', href: '#' },
      { label: 'Condizioni', href: '#' }
    ]
  }
]
</script>

<template>
  <footer class="mt-16">
    <!-- Top dark strip -->
    <section class="bg-slate-900 text-white">
      <div class="mx-auto w-full max-w-7xl px-4 py-6 sm:px-6 lg:px-8">
        <div class="flex flex-col gap-4 min-[800px]:flex-row min-[800px]:items-center min-[800px]:justify-between">
          <p class="max-w-3xl text-sm font-semibold">
            Le aziende più importanti scelgono <span class="text-violet-300">Udemy Business</span>
            per fornire ai propri dipendenti le competenze professionali più richieste.
          </p>

          <!-- Logos placeholder -->
          <div class="flex items-center gap-6 text-slate-300">
            <span class="font-semibold">Nasdaq</span>
            <span class="font-semibold">VW</span>
            <span class="font-semibold">NetApp</span>
            <span class="font-semibold">eventbrite</span>
          </div>
        </div>
      </div>
      <div class="h-px w-full bg-white/15" />
    </section>

    <!-- Middle area: links grid OR accordion -->
    <section class="bg-slate-800 text-white">
      <div class="mx-auto w-full max-w-7xl px-4 py-10 sm:px-6 lg:px-8">
        <h2 class="text-base font-bold">
          Esplora le competenze e le certificazioni più popolari
        </h2>

        <!-- Desktop grid (>= 800px) -->
        <div class="mt-8 hidden min-[800px]:grid min-[800px]:grid-cols-4 min-[800px]:gap-10">
          <div v-for="sec in sections" :key="sec.title">
            <h3 class="text-sm font-semibold">{{ sec.title }}</h3>
            <ul class="mt-4 space-y-2 text-sm text-slate-200">
              <li v-for="l in sec.links" :key="l.label">
                <a :href="l.href" class="hover:underline">{{ l.label }}</a>
              </li>
            </ul>
          </div>
        </div>

        <!-- Mobile accordion (< 800px) -->
        <div class="mt-6 min-[800px]:hidden">
          <div class="divide-y divide-white/15 rounded-lg border border-white/10">
            <details v-for="sec in sections" :key="sec.title" class="group">
              <summary
                class="flex cursor-pointer list-none items-center justify-between gap-4 px-4 py-4 text-sm font-semibold"
              >
                <span>{{ sec.title }}</span>
                <span class="text-slate-300 transition group-open:rotate-180" aria-hidden="true">▾</span>
              </summary>

              <div class="px-4 pb-4">
                <ul class="space-y-2 text-sm text-slate-200">
                  <li v-for="l in sec.links" :key="l.label">
                    <a :href="l.href" class="hover:underline">{{ l.label }}</a>
                  </li>
                </ul>
              </div>
            </details>
          </div>
        </div>

        <div class="mt-10 h-px w-full bg-white/15" />

        <!-- Bottom columns -->
        <div class="mt-10 grid grid-cols-2 gap-10 min-[800px]:grid-cols-4">
          <div v-for="col in bottomColumns" :key="col.title">
            <h3 class="text-sm font-semibold">{{ col.title }}</h3>
            <ul class="mt-4 space-y-2 text-sm text-slate-200">
              <li v-for="l in col.links" :key="l.label">
                <a :href="l.href" class="hover:underline">{{ l.label }}</a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <div class="h-px w-full bg-white/15" />

      <!-- Very bottom bar -->
      <div class="mx-auto w-full max-w-7xl px-4 py-6 sm:px-6 lg:px-8">
        <div class="flex flex-col gap-4 min-[800px]:flex-row min-[800px]:items-center min-[800px]:justify-between">
          <div class="flex items-center gap-3">
            <span class="text-lg font-extrabold">udemy</span>
            <span class="text-sm text-slate-300">© 2026 Udemy, Inc.</span>
          </div>

          <a href="#" class="text-sm text-slate-200 hover:underline">
            Impostazioni dei cookie
          </a>

          <button
            type="button"
            class="inline-flex items-center gap-2 self-start rounded-md border border-white/20 px-3 py-2 text-sm font-semibold text-white hover:bg-white/10 min-[800px]:self-auto"
            aria-label="Change language"
          >
            🌐 Italiano
          </button>
        </div>
      </div>
    </section>
  </footer>
</template>
