<script setup lang="ts">
// Hero for the homepage. Uses a gradient + Unsplash-style SVG pattern as the
// placeholder background so the mockup works without external image assets.
</script>

<template>
  <section class="relative isolate overflow-hidden bg-brand-900 text-white">
    <!-- Background: gradient + pattern + soft blobs -->
    <div class="absolute inset-0 -z-10">
      <div
        class="absolute inset-0 bg-gradient-to-br from-brand-900 via-brand-800 to-leaf-900"
      />
      <div
        class="absolute inset-0 opacity-25 mix-blend-overlay"
        style="background-image: radial-gradient(circle at 20% 30%, rgba(255,255,255,0.25) 0, transparent 40%), radial-gradient(circle at 80% 70%, rgba(73,203,130,0.35) 0, transparent 45%);"
      />
      <svg
        aria-hidden="true"
        class="absolute inset-0 h-full w-full opacity-[0.08]"
        xmlns="http://www.w3.org/2000/svg"
      >
        <defs>
          <pattern id="hero-grid" width="48" height="48" patternUnits="userSpaceOnUse">
            <path d="M48 0H0V48" fill="none" stroke="white" stroke-width="0.7" />
          </pattern>
        </defs>
        <rect width="100%" height="100%" fill="url(#hero-grid)" />
      </svg>
    </div>

    <div class="mx-auto grid max-w-7xl gap-12 px-4 py-24 sm:px-6 lg:grid-cols-12 lg:gap-8 lg:px-8 lg:py-32">
      <div class="lg:col-span-7">
        <span class="inline-flex items-center gap-2 rounded-full border border-white/20 bg-white/10 px-4 py-1.5 text-xs font-semibold uppercase tracking-wider backdrop-blur">
          <span class="h-2 w-2 rounded-full bg-leaf-400" />
          Global Humanitarian &amp; Environmental Aid
        </span>

        <h1 class="mt-6 text-4xl font-extrabold leading-[1.05] tracking-tight sm:text-5xl lg:text-6xl">
          Empowering Communities,
          <span class="bg-gradient-to-r from-leaf-300 to-sunset-400 bg-clip-text text-transparent">
            Protecting the Future.
          </span>
        </h1>

        <p class="mt-6 max-w-2xl text-lg leading-relaxed text-brand-100 sm:text-xl">
          From disaster-struck coastlines to remote villages without clean water,
          Horizon Aid partners with local leaders to deliver relief that lasts
          long after the news cameras leave.
        </p>

        <div class="mt-10 flex flex-col gap-3 sm:flex-row">
          <NuxtLink
            to="/about"
            class="inline-flex items-center justify-center gap-2 rounded-full border border-white/30 bg-white/10 px-7 py-3.5 text-base font-semibold text-white backdrop-blur transition hover:bg-white/20"
          >
            Our Mission
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round" class="h-4 w-4">
              <path d="M5 12h14M13 5l7 7-7 7" />
            </svg>
          </NuxtLink>
          <NuxtLink
            to="/donate"
            class="inline-flex items-center justify-center gap-2 rounded-full bg-sunset-500 px-7 py-3.5 text-base font-bold text-white shadow-lg shadow-sunset-500/30 transition hover:-translate-y-0.5 hover:bg-sunset-600 hover:shadow-xl"
          >
            Donate
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="h-4 w-4">
              <path d="M11.645 20.91 12 21l.355-.09C17.79 19.2 22 15.05 22 9.75 22 6.57 19.43 4 16.25 4A5.24 5.24 0 0 0 12 6.09 5.24 5.24 0 0 0 7.75 4C4.57 4 2 6.57 2 9.75c0 5.3 4.21 9.45 9.645 11.16Z" />
            </svg>
          </NuxtLink>
        </div>

        <!-- Trust bar -->
        <div class="mt-12 flex flex-wrap items-center gap-x-8 gap-y-3 text-xs uppercase tracking-wider text-brand-200">
          <span class="flex items-center gap-2">
            <svg class="h-4 w-4 text-leaf-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round">
              <path d="m9 12 2 2 4-4" /><circle cx="12" cy="12" r="10" />
            </svg>
            4-Star Charity Navigator
          </span>
          <span class="flex items-center gap-2">
            <svg class="h-4 w-4 text-leaf-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round">
              <path d="m9 12 2 2 4-4" /><circle cx="12" cy="12" r="10" />
            </svg>
            GuideStar Platinum Transparency
          </span>
          <span class="flex items-center gap-2">
            <svg class="h-4 w-4 text-leaf-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round">
              <path d="m9 12 2 2 4-4" /><circle cx="12" cy="12" r="10" />
            </svg>
            UN ECOSOC Consultative Status
          </span>
        </div>
      </div>

      <!-- Decorative stat card -->
      <div class="relative hidden lg:col-span-5 lg:block">
        <div class="animate-floaty absolute right-0 top-8 w-full max-w-sm rounded-3xl border border-white/15 bg-white/10 p-6 shadow-2xl backdrop-blur-xl">
          <p class="text-xs font-semibold uppercase tracking-wider text-leaf-300">
            Live from the field
          </p>
          <p class="mt-2 text-2xl font-bold leading-snug">
            Clean water delivered to 12 villages in rural Madagascar this week.
          </p>
          <div class="mt-5 flex items-center gap-3">
            <div class="flex -space-x-2">
              <span class="h-9 w-9 rounded-full border-2 border-brand-900 bg-gradient-to-br from-leaf-400 to-brand-400" />
              <span class="h-9 w-9 rounded-full border-2 border-brand-900 bg-gradient-to-br from-sunset-400 to-brand-500" />
              <span class="h-9 w-9 rounded-full border-2 border-brand-900 bg-gradient-to-br from-brand-400 to-leaf-500" />
            </div>
            <p class="text-sm text-brand-100">
              Field team reporting · 2h ago
            </p>
          </div>
        </div>

        <div class="absolute bottom-0 left-0 w-72 rounded-3xl border border-white/15 bg-brand-900/60 p-5 shadow-xl backdrop-blur-xl">
          <div class="flex items-center gap-3">
            <span class="flex h-10 w-10 items-center justify-center rounded-xl bg-leaf-500/20 text-leaf-300">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-5 w-5">
                <path d="M12 2v20M2 12h20" stroke-linecap="round" />
              </svg>
            </span>
            <div>
              <p class="text-lg font-bold">$0.92 of every $1</p>
              <p class="text-xs text-brand-200">goes directly to the field</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
