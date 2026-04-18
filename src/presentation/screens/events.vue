<script setup lang="ts">
useHead({ title: 'Events — RuralNexus' });

const upcomingEvents = [
  {
    id: 'e1',
    title: 'Rural Food Systems Innovation Summit 2026',
    type: 'Conference',
    date: 'June 12–14, 2026',
    location: 'Geneva, Switzerland',
    description:
      'A flagship two-day summit bringing together agronomists, policy-makers, and NGO practitioners to share emerging models for climate-resilient food systems across Sub-Saharan Africa and Central Asia.',
    spotsLeft: 41,
    gradient: 'from-primary to-leaf-600',
    virtual: false,
  },
  {
    id: 'e2',
    title: 'Webinar: Measuring Impact in Participatory Research',
    type: 'Webinar',
    date: 'May 8, 2026',
    location: 'Online',
    description:
      'A free one-hour webinar for researchers and NGO practitioners exploring how to design monitoring & evaluation frameworks that honour community participation without sacrificing scientific rigour.',
    spotsLeft: 210,
    gradient: 'from-cyan to-leaf-500',
    virtual: true,
  },
  {
    id: 'e3',
    title: 'Living Labs Field Visit — Western Kenya',
    type: 'Field Visit',
    date: 'July 3–7, 2026',
    location: 'Kisumu, Kenya',
    description:
      'A week-long immersive field visit for PA3 partners and selected fellows to observe our on-farm trials with drought-tolerant maize varieties and soil-health monitoring protocols.',
    spotsLeft: 8,
    gradient: 'from-leaf-700 to-primary-container',
    virtual: false,
  },
  {
    id: 'e4',
    title: 'Volunteer Orientation — Q3 2026 Cohort',
    type: 'Orientation',
    date: 'August 4, 2026',
    location: 'Online',
    description:
      'Welcoming our newest cohort of volunteers. This interactive session covers RuralNexus mission, program area introductions, tool access, and a live Q&A with program coordinators.',
    spotsLeft: 55,
    gradient: 'from-primary-container to-cyan',
    virtual: true,
  },
  {
    id: 'e5',
    title: 'Grant Writing Masterclass for NGOs',
    type: 'Workshop',
    date: 'September 17, 2026',
    location: 'Online',
    description:
      'A half-day intensive workshop covering EU Horizon proposal structuring, budget justification standards, and common reviewer pitfalls — facilitated by the RuralNexus PA1 Acquisition team.',
    spotsLeft: 30,
    gradient: 'from-leaf-600 to-primary',
    virtual: true,
  },
  {
    id: 'e6',
    title: 'Annual Partners Meeting 2026',
    type: 'Partner Event',
    date: 'October 21–22, 2026',
    location: 'Nairobi, Kenya',
    description:
      'Invitation-only annual convening for institutional partners, funders, and fellows. Includes programme reviews, strategy sessions, and the RuralNexus Impact Awards ceremony.',
    spotsLeft: 0,
    gradient: 'from-sunset to-primary-container',
    virtual: false,
  },
];

const pastEvents = [
  {
    title: 'Soil Health & Digital Sensing Workshop',
    date: 'March 2026',
    location: 'Dakar, Senegal',
    type: 'Workshop',
    attendees: 78,
  },
  {
    title: 'Policy Roundtable: Rural SDG Alignment',
    date: 'February 2026',
    location: 'Brussels, Belgium',
    type: 'Roundtable',
    attendees: 44,
  },
  {
    title: 'Webinar: Remote Sensing for Smallholder Agriculture',
    date: 'January 2026',
    location: 'Online',
    type: 'Webinar',
    attendees: 312,
  },
  {
    title: 'Cassava Belt Field Research Exchange',
    date: 'December 2025',
    location: 'Ibadan, Nigeria',
    type: 'Field Visit',
    attendees: 22,
  },
];

const typeColors: Record<string, string> = {
  Conference: 'bg-primary/10 text-primary',
  Webinar: 'bg-cyan/10 text-cyan',
  'Field Visit': 'bg-leaf/10 text-leaf',
  Orientation: 'bg-amber-500/10 text-amber-600',
  Workshop: 'bg-sunset/10 text-sunset',
  'Partner Event': 'bg-primary-container/20 text-on-primary-container',
  Roundtable: 'bg-primary-container/20 text-on-primary-container',
};
</script>

<template>
  <div class="flex flex-col bg-surface">
    <!-- Hero -->
    <section class="relative overflow-hidden bg-gradient-to-br from-primary-container to-primary py-20 text-white">
      <div class="hex-mask absolute -right-20 top-0 h-80 w-80 bg-white opacity-[0.04] pointer-events-none" />
      <div class="relative z-10 mx-auto max-w-4xl px-4 text-center sm:px-6 lg:px-8">
        <p class="text-sm font-bold uppercase tracking-widest opacity-70">Gatherings & Learning</p>
        <h1 class="mt-4 font-display text-4xl font-bold md:text-5xl">Events & Convenings</h1>
        <p class="mx-auto mt-5 max-w-2xl font-body text-lg leading-relaxed opacity-85">
          From international summits to online webinars, RuralNexus brings practitioners, researchers,
          and communities together to share knowledge and build collective capacity.
        </p>
      </div>
    </section>

    <!-- Upcoming events -->
    <section class="py-24 bg-surface">
      <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="mb-14 flex flex-col gap-4 sm:flex-row sm:items-end sm:justify-between">
          <div>
            <p class="text-sm font-bold uppercase tracking-widest text-primary">Upcoming</p>
            <h2 class="mt-2 font-display text-3xl font-bold text-on-surface">Events in 2026</h2>
          </div>
          <div class="flex gap-2">
            <button
              type="button"
              class="rounded-full border border-outline-variant px-4 py-2 text-sm font-semibold text-on-surface hover:bg-surface-container-low transition"
            >
              All Types
            </button>
            <button
              type="button"
              class="rounded-full border border-outline-variant px-4 py-2 text-sm font-semibold text-on-surface hover:bg-surface-container-low transition"
            >
              Virtual Only
            </button>
          </div>
        </div>

        <div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
          <article
            v-for="event in upcomingEvents"
            :key="event.id"
            class="group flex flex-col overflow-hidden rounded-2xl bg-surface-container-lowest ambient-shadow transition hover:-translate-y-1"
          >
            <!-- Gradient banner -->
            <div
              class="relative h-36 bg-gradient-to-br"
              :class="event.gradient"
            >
              <div class="absolute inset-0 opacity-20 mix-blend-overlay" style="background-image: radial-gradient(circle at 30% 40%, white 0, transparent 55%);" />
              <!-- Type badge -->
              <div class="absolute left-4 top-4">
                <span
                  class="rounded-full bg-white/90 px-3 py-1 text-[11px] font-bold uppercase tracking-wider text-on-surface"
                  :class="typeColors[event.type]"
                >
                  {{ event.type }}
                </span>
              </div>
              <!-- Virtual tag -->
              <div v-if="event.virtual" class="absolute bottom-4 right-4">
                <span class="rounded-full bg-black/30 px-2.5 py-1 text-[11px] font-semibold uppercase tracking-wider text-white backdrop-blur-sm">
                  Virtual
                </span>
              </div>
            </div>

            <div class="flex flex-1 flex-col p-6">
              <!-- Meta -->
              <div class="flex flex-wrap items-center gap-x-3 gap-y-1 text-xs font-medium text-on-surface-variant">
                <span class="flex items-center gap-1">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-3.5 w-3.5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
                  {{ event.date }}
                </span>
                <span class="h-1 w-1 rounded-full bg-outline-variant" />
                <span class="flex items-center gap-1">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-3.5 w-3.5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"/><circle cx="12" cy="10" r="3"/></svg>
                  {{ event.location }}
                </span>
              </div>

              <h3 class="mt-3 font-display text-lg font-bold leading-snug text-on-surface">
                {{ event.title }}
              </h3>
              <p class="mt-2 flex-1 font-body text-sm leading-relaxed text-on-surface-variant">
                {{ event.description }}
              </p>

              <!-- Footer -->
              <div class="mt-6 flex items-center justify-between">
                <span
                  v-if="event.spotsLeft > 0"
                  class="text-xs font-semibold"
                  :class="event.spotsLeft < 15 ? 'text-sunset' : 'text-on-surface-variant'"
                >
                  {{ event.spotsLeft < 15 ? '🔥' : '' }} {{ event.spotsLeft }} spots left
                </span>
                <span v-else class="text-xs font-semibold text-on-surface-variant opacity-50">
                  Invitation only
                </span>
                <button
                  type="button"
                  :disabled="event.spotsLeft === 0"
                  class="rounded-lg bg-primary px-4 py-2 text-sm font-bold text-on-primary transition hover:opacity-90 disabled:cursor-not-allowed disabled:opacity-40"
                >
                  {{ event.spotsLeft > 0 ? 'Register' : 'Closed' }}
                </button>
              </div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- Past events archive -->
    <section class="bg-surface-container-low py-20">
      <div class="mx-auto max-w-5xl px-4 sm:px-6 lg:px-8">
        <div class="mb-10">
          <p class="text-sm font-bold uppercase tracking-widest text-primary">Archive</p>
          <h2 class="mt-2 font-display text-2xl font-bold text-on-surface md:text-3xl">Past Events</h2>
        </div>

        <div class="overflow-hidden rounded-2xl bg-surface-container-lowest ambient-shadow">
          <table class="w-full text-sm">
            <thead>
              <tr class="border-b border-outline-variant/20 bg-surface-container-low">
                <th class="px-6 py-4 text-left text-xs font-bold uppercase tracking-wider text-on-surface-variant">Event</th>
                <th class="hidden px-6 py-4 text-left text-xs font-bold uppercase tracking-wider text-on-surface-variant sm:table-cell">Type</th>
                <th class="hidden px-6 py-4 text-left text-xs font-bold uppercase tracking-wider text-on-surface-variant md:table-cell">Date</th>
                <th class="px-6 py-4 text-left text-xs font-bold uppercase tracking-wider text-on-surface-variant">Location</th>
                <th class="hidden px-6 py-4 text-right text-xs font-bold uppercase tracking-wider text-on-surface-variant lg:table-cell">Attendees</th>
              </tr>
            </thead>
            <tbody class="divide-y divide-outline-variant/10">
              <tr
                v-for="past in pastEvents"
                :key="past.title"
                class="hover:bg-surface-container-low transition-colors"
              >
                <td class="px-6 py-4 font-body font-medium text-on-surface">{{ past.title }}</td>
                <td class="hidden px-6 py-4 sm:table-cell">
                  <span class="rounded-full px-2.5 py-1 text-[11px] font-semibold uppercase" :class="typeColors[past.type] ?? 'bg-surface-container-low text-on-surface-variant'">
                    {{ past.type }}
                  </span>
                </td>
                <td class="hidden px-6 py-4 text-on-surface-variant md:table-cell">{{ past.date }}</td>
                <td class="px-6 py-4 text-on-surface-variant">{{ past.location }}</td>
                <td class="hidden px-6 py-4 text-right font-semibold text-on-surface lg:table-cell">{{ past.attendees }}</td>
              </tr>
            </tbody>
          </table>
        </div>

        <div class="mt-6 text-center">
          <button type="button" class="rounded-full border border-outline-variant px-6 py-3 text-sm font-semibold text-on-surface hover:bg-surface-container-lowest transition">
            Load more past events
          </button>
        </div>
      </div>
    </section>

    <!-- CTA -->
    <section class="bg-primary py-16 text-on-primary">
      <div class="mx-auto max-w-3xl px-4 text-center sm:px-6 lg:px-8">
        <h2 class="font-display text-2xl font-bold md:text-3xl">Want to speak or host an event?</h2>
        <p class="mx-auto mt-4 max-w-lg font-body opacity-80">
          We welcome collaboration proposals from research institutions, universities, and
          development organisations to co-host or co-present at our events.
        </p>
        <NuxtLink
          to="/contact"
          class="mt-8 inline-flex items-center gap-2 rounded-lg bg-white px-8 py-4 font-bold text-primary shadow-lg transition hover:-translate-y-0.5"
        >
          Get in Touch
        </NuxtLink>
      </div>
    </section>
  </div>
</template>
