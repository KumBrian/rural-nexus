<script setup lang="ts">
useHead({ title: 'Programs — Horizon Aid' })

const programs = [
  {
    title: 'Clean Water & Sanitation',
    description:
      'Solar-powered wells, rainwater harvesting, and community-run hygiene programs in water-scarce regions.',
    stat: '312 wells',
    statLabel: 'drilled since 2004',
    gradient: 'from-brand-700 to-leaf-500',
    icon: 'drop',
  },
  {
    title: 'Climate & Reforestation',
    description:
      'Native-species tree planting, watershed restoration, and partnerships with indigenous land stewards.',
    stat: '1.2M trees',
    statLabel: 'planted across 4 continents',
    gradient: 'from-leaf-600 to-brand-500',
    icon: 'leaf',
  },
  {
    title: 'Emergency Relief',
    description:
      'Rapid-response shelter, water, and medical supplies in the first 72 hours after a humanitarian crisis.',
    stat: '48 responses',
    statLabel: 'deployed since 2015',
    gradient: 'from-sunset-500 to-brand-700',
    icon: 'alert',
  },
  {
    title: 'Education',
    description:
      'Teacher training, learning materials, and scholarships — delivered through local schools, not replacing them.',
    stat: '9,400 children',
    statLabel: 'supported this year',
    gradient: 'from-brand-600 to-sunset-400',
    icon: 'book',
  },
  {
    title: 'Food Security',
    description:
      'Drought-resistant seeds, agricultural training, and grain banks co-managed with smallholder farmers.',
    stat: '22,000 farmers',
    statLabel: 'in our training network',
    gradient: 'from-leaf-700 to-brand-600',
    icon: 'wheat',
  },
  {
    title: 'Maternal & Child Health',
    description:
      'Solar-powered rural clinics, midwife training, and nutrition programs for mothers and young children.',
    stat: '14 clinics',
    statLabel: 'operating year-round',
    gradient: 'from-brand-800 to-leaf-600',
    icon: 'heart',
  },
]
</script>

<template>
  <div>
    <!-- Hero -->
    <section class="bg-gradient-to-b from-brand-50/80 to-white py-20 sm:py-24">
      <div class="mx-auto max-w-4xl px-4 text-center sm:px-6 lg:px-8">
        <p class="text-sm font-bold uppercase tracking-wider text-brand-600">
          What we do
        </p>
        <h1 class="mt-3 text-4xl font-extrabold tracking-tight text-brand-900 sm:text-5xl">
          Six programs, one mission.
        </h1>
        <p class="mt-5 text-lg leading-relaxed text-brand-900/70">
          Every program is run in partnership with local organizations and
          designed to outlast any single grant cycle. Here's where your
          support goes.
        </p>
      </div>
    </section>

    <!-- Programs grid -->
    <section class="bg-white pb-24">
      <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
          <article
            v-for="program in programs"
            :key="program.title"
            class="group relative flex h-full flex-col overflow-hidden rounded-3xl border border-brand-100 bg-white shadow-sm transition hover:-translate-y-1 hover:shadow-xl"
          >
            <div
              class="relative flex h-40 items-end bg-gradient-to-br p-6"
              :class="program.gradient"
            >
              <div class="absolute inset-0 opacity-25 mix-blend-overlay" style="background-image: radial-gradient(circle at 30% 35%, white 0, transparent 50%);" />
              <span class="relative flex h-14 w-14 items-center justify-center rounded-2xl bg-white/95 text-brand-800 shadow-lg">
                <svg v-if="program.icon === 'drop'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-7 w-7">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M12 2s6 7 6 12a6 6 0 0 1-12 0c0-5 6-12 6-12Z" />
                </svg>
                <svg v-else-if="program.icon === 'leaf'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-7 w-7">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M11 20A7 7 0 0 1 4 13V4h9a7 7 0 0 1 0 14h-2ZM4 4l16 16" />
                </svg>
                <svg v-else-if="program.icon === 'alert'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-7 w-7">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M12 9v4m0 4h.01M10.3 3.86 1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0Z" />
                </svg>
                <svg v-else-if="program.icon === 'book'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-7 w-7">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20M4 19.5A2.5 2.5 0 0 0 6.5 22H20V2H6.5A2.5 2.5 0 0 0 4 4.5v15Z" />
                </svg>
                <svg v-else-if="program.icon === 'wheat'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-7 w-7">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M12 22V8m0 0c-2-3-5-3-5-3s0 3 2 5 3 0 3-2Zm0 0c2-3 5-3 5-3s0 3-2 5-3 0-3-2Zm-3 7c-2-2-5-2-5-2s0 3 2 5 3 0 3-3Zm6 0c2-2 5-2 5-2s0 3-2 5-3 0-3-3Z" />
                </svg>
                <svg v-else xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-7 w-7">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78Z" />
                </svg>
              </span>
            </div>
            <div class="flex flex-1 flex-col p-6">
              <h3 class="text-xl font-bold text-brand-900">{{ program.title }}</h3>
              <p class="mt-2 flex-1 text-sm leading-relaxed text-brand-900/70">
                {{ program.description }}
              </p>
              <div class="mt-6 rounded-2xl bg-brand-50 p-4">
                <p class="text-2xl font-extrabold text-brand-900">
                  {{ program.stat }}
                </p>
                <p class="text-xs font-semibold uppercase tracking-wider text-brand-600">
                  {{ program.statLabel }}
                </p>
              </div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="bg-brand-50/60 py-20">
      <div class="mx-auto max-w-3xl px-4 text-center sm:px-6 lg:px-8">
        <h2 class="text-3xl font-extrabold tracking-tight text-brand-900 sm:text-4xl">
          Fund the work that moves you.
        </h2>
        <p class="mt-4 text-lg text-brand-900/70">
          Choose a program or let us direct your gift where it's needed most.
        </p>
        <NuxtLink
          to="/donate"
          class="mt-8 inline-flex items-center gap-2 rounded-full bg-sunset-500 px-8 py-4 text-base font-bold text-white shadow-lg shadow-sunset-500/30 transition hover:-translate-y-0.5 hover:bg-sunset-600"
        >
          Donate now
        </NuxtLink>
      </div>
    </section>
  </div>
</template>
