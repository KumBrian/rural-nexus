<script setup lang="ts">
useHead({ title: 'Field Stories — Horizon Aid' })

const featured = {
  title: "How a single well changed everything for Andavadoaka",
  excerpt:
    "When the old hand-pump failed in the winter of 2022, the women of this coastal Madagascan village were walking six kilometres each morning for water. Eighteen months later, everything looks different.",
  location: 'Madagascar',
  program: 'Clean Water',
  readTime: '8 min read',
  author: 'Fanja Ratsimbazafy',
  date: 'March 2026',
  gradient: 'from-brand-700 via-brand-600 to-leaf-500',
}

const stories = [
  {
    title: "'The forest is coming back': a decade of reforestation in the Xingu basin",
    excerpt:
      'Indigenous partners have planted 250,000 native trees since 2014. We spent a week with the team seeing what that actually looks like on the ground.',
    location: 'Brazil',
    program: 'Climate',
    readTime: '6 min read',
    date: 'February 2026',
    gradient: 'from-leaf-600 to-brand-500',
  },
  {
    title: 'After the floods: rebuilding Sindh one shelter kit at a time',
    excerpt:
      "Record monsoon rains displaced 4,500 families in southern Pakistan. A field update from our emergency response team six months in.",
    location: 'Pakistan',
    program: 'Emergency',
    readTime: '5 min read',
    date: 'January 2026',
    gradient: 'from-sunset-500 to-brand-700',
  },
  {
    title: 'Why we stopped building schools — and what we do now instead',
    excerpt:
      'A hard lesson from Malawi on what sustainable education work really looks like. Spoiler: it rarely involves ribbon-cutting ceremonies.',
    location: 'Malawi',
    program: 'Education',
    readTime: '7 min read',
    date: 'December 2025',
    gradient: 'from-brand-600 to-sunset-400',
  },
  {
    title: 'The solar clinic that outlasted the grant',
    excerpt:
      'Five years after the funding ended, the Kisumu maternal health clinic still runs — on sunlight, local staff, and a little bit of stubbornness.',
    location: 'Kenya',
    program: 'Health',
    readTime: '6 min read',
    date: 'December 2025',
    gradient: 'from-brand-800 to-leaf-600',
  },
  {
    title: 'Listening before building: what we learned in the Andes',
    excerpt:
      'Our Peru program manager on why the first six months of any project should involve zero construction — and a lot of conversation.',
    location: 'Peru',
    program: 'Food Security',
    readTime: '4 min read',
    date: 'November 2025',
    gradient: 'from-leaf-700 to-brand-600',
  },
  {
    title: 'Meet the partners: Association Tanjona',
    excerpt:
      'A conversation with the Madagascar-based collective that runs 70% of our clean-water work on the island.',
    location: 'Madagascar',
    program: 'Partners',
    readTime: '5 min read',
    date: 'November 2025',
    gradient: 'from-sunset-400 to-brand-500',
  },
]
</script>

<template>
  <div>
    <!-- Page header -->
    <section class="bg-white pt-20 pb-8">
      <div class="mx-auto max-w-4xl px-4 text-center sm:px-6 lg:px-8">
        <p class="text-sm font-bold uppercase tracking-wider text-brand-600">
          Field Stories
        </p>
        <h1 class="mt-3 text-4xl font-extrabold tracking-tight text-brand-900 sm:text-5xl">
          Dispatches from the work.
        </h1>
        <p class="mt-5 text-lg text-brand-900/70">
          First-hand reports from our partners and field teams. No filler,
          no fundraising-speak — just what's actually happening on the ground.
        </p>
      </div>
    </section>

    <!-- Featured story -->
    <section class="bg-white pt-8 pb-16">
      <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <article class="group grid overflow-hidden rounded-3xl border border-brand-100 bg-white shadow-sm transition hover:shadow-xl lg:grid-cols-2">
          <div
            class="relative aspect-[16/10] bg-gradient-to-br lg:aspect-auto"
            :class="featured.gradient"
          >
            <div class="absolute inset-0 opacity-30 mix-blend-overlay" style="background-image: radial-gradient(circle at 25% 35%, white 0, transparent 50%), radial-gradient(circle at 75% 75%, white 0, transparent 45%);" />
            <svg aria-hidden="true" class="absolute inset-0 h-full w-full opacity-[0.15]" xmlns="http://www.w3.org/2000/svg">
              <defs>
                <pattern id="featured-grid" width="40" height="40" patternUnits="userSpaceOnUse">
                  <path d="M40 0H0V40" fill="none" stroke="white" stroke-width="0.6" />
                </pattern>
              </defs>
              <rect width="100%" height="100%" fill="url(#featured-grid)" />
            </svg>
            <div class="absolute left-6 top-6">
              <span class="rounded-full bg-white/95 px-3 py-1 text-[11px] font-bold uppercase tracking-wider text-brand-700">
                Featured
              </span>
            </div>
          </div>
          <div class="flex flex-col justify-center p-8 sm:p-10 lg:p-14">
            <div class="flex flex-wrap items-center gap-2 text-xs font-semibold uppercase tracking-wider text-brand-600">
              <span>{{ featured.program }}</span>
              <span class="h-1 w-1 rounded-full bg-brand-300" />
              <span>{{ featured.location }}</span>
              <span class="h-1 w-1 rounded-full bg-brand-300" />
              <span>{{ featured.readTime }}</span>
            </div>
            <h2 class="mt-4 text-2xl font-extrabold leading-snug text-brand-900 sm:text-3xl">
              {{ featured.title }}
            </h2>
            <p class="mt-4 text-base leading-relaxed text-brand-900/75">
              {{ featured.excerpt }}
            </p>
            <div class="mt-6 flex items-center gap-3">
              <span class="h-10 w-10 rounded-full bg-gradient-to-br from-brand-500 to-leaf-400" />
              <div class="text-sm">
                <p class="font-bold text-brand-900">{{ featured.author }}</p>
                <p class="text-brand-900/60">{{ featured.date }}</p>
              </div>
            </div>
            <a
              href="#"
              class="mt-8 inline-flex w-fit items-center gap-2 rounded-full bg-brand-900 px-6 py-3 text-sm font-bold text-white transition hover:bg-brand-700"
            >
              Read the story
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round" class="h-4 w-4">
                <path d="M5 12h14M13 5l7 7-7 7" />
              </svg>
            </a>
          </div>
        </article>
      </div>
    </section>

    <!-- Story grid -->
    <section class="bg-brand-50/50 py-20">
      <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="flex items-end justify-between">
          <h2 class="text-2xl font-extrabold tracking-tight text-brand-900 sm:text-3xl">
            More from the field
          </h2>
          <button
            type="button"
            class="hidden rounded-full border border-brand-200 bg-white px-4 py-2 text-sm font-semibold text-brand-900 hover:border-brand-600 sm:inline-flex"
          >
            All programs
          </button>
        </div>

        <div class="mt-10 grid gap-6 md:grid-cols-2 lg:grid-cols-3">
          <article
            v-for="story in stories"
            :key="story.title"
            class="group flex h-full flex-col overflow-hidden rounded-3xl border border-brand-100 bg-white shadow-sm transition hover:-translate-y-1 hover:shadow-xl"
          >
            <div
              class="relative aspect-[16/10] overflow-hidden bg-gradient-to-br"
              :class="story.gradient"
            >
              <div class="absolute inset-0 opacity-25 mix-blend-overlay" style="background-image: radial-gradient(circle at 35% 40%, white 0, transparent 50%);" />
              <div class="absolute left-4 top-4">
                <span class="rounded-full bg-white/95 px-3 py-1 text-[11px] font-bold uppercase tracking-wider text-brand-700">
                  {{ story.program }}
                </span>
              </div>
              <div class="absolute bottom-4 left-4 flex items-center gap-1.5 text-xs font-semibold text-white/90">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-4 w-4">
                  <path d="M12 21s-7-4.5-7-11a7 7 0 0 1 14 0c0 6.5-7 11-7 11Z" stroke-linecap="round" stroke-linejoin="round" />
                  <circle cx="12" cy="10" r="2.5" />
                </svg>
                {{ story.location }}
              </div>
            </div>
            <div class="flex flex-1 flex-col p-6">
              <h3 class="text-lg font-bold leading-snug text-brand-900">
                {{ story.title }}
              </h3>
              <p class="mt-2 flex-1 text-sm leading-relaxed text-brand-900/70">
                {{ story.excerpt }}
              </p>
              <div class="mt-5 flex items-center justify-between text-xs text-brand-900/60">
                <span>{{ story.date }}</span>
                <span>{{ story.readTime }}</span>
              </div>
            </div>
          </article>
        </div>

        <!-- Load more -->
        <div class="mt-12 flex justify-center">
          <button
            type="button"
            class="inline-flex items-center gap-2 rounded-full border border-brand-200 bg-white px-6 py-3 text-sm font-bold text-brand-900 hover:border-brand-600 hover:text-brand-700"
          >
            Load more stories
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round" class="h-4 w-4">
              <path d="M12 5v14M5 12h14" />
            </svg>
          </button>
        </div>
      </div>
    </section>
  </div>
</template>
