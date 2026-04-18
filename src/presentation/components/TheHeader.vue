<script setup lang="ts">
const mobileOpen = ref(false)

const navLinks = [
  { label: 'Home', to: '/' },
  { label: 'About', to: '/about' },
  { label: 'Programs', to: '/programs' },
  { label: 'Stories', to: '/stories' },
  { label: 'Volunteer', to: '/volunteer' },
  { label: 'Events', to: '/events' },
  { label: 'Gallery', to: '/gallery' },
  { label: 'Impact', to: '/impact' },
  { label: 'Contact', to: '/contact' },
]

const route = useRoute()
watch(() => route.fullPath, () => {
  mobileOpen.value = false
})
</script>

<template>
  <header
    class="sticky top-0 z-40 w-full border-b border-brand-100/60 bg-white/90 backdrop-blur supports-[backdrop-filter]:bg-white/70"
  >
    <div class="mx-auto flex max-w-7xl items-center justify-between px-4 py-4 sm:px-6 lg:px-8">
      <!-- Logo -->
      <NuxtLink
        to="/"
        class="flex items-center gap-2 text-brand-900"
        aria-label="Horizon Aid home"
      >
        <span
          class="flex h-10 w-10 items-center justify-center rounded-xl bg-gradient-to-br from-brand-700 to-leaf-500 text-white shadow-sm"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2.2"
            stroke-linecap="round"
            stroke-linejoin="round"
            class="h-5 w-5"
          >
            <path d="M12 21s-7-4.5-7-11a7 7 0 0 1 14 0c0 6.5-7 11-7 11Z" />
            <circle cx="12" cy="10" r="2.5" />
          </svg>
        </span>
        <div class="leading-tight">
          <p class="text-lg font-bold tracking-tight">Horizon Aid</p>
          <p class="text-[11px] font-medium uppercase tracking-wider text-brand-500">
            Humanitarian &amp; Environmental Relief
          </p>
        </div>
      </NuxtLink>

      <!-- Desktop nav -->
      <nav class="hidden items-center gap-0.5 lg:flex">
        <NuxtLink
          v-for="link in navLinks"
          :key="link.to"
          :to="link.to"
          class="rounded-full px-3 py-2 text-sm font-semibold text-brand-900/80 transition hover:bg-brand-50 hover:text-brand-900"
          active-class="bg-brand-50 text-brand-900"
        >
          {{ link.label }}
        </NuxtLink>
        <NuxtLink
          to="/donate"
          class="ml-3 inline-flex items-center gap-2 rounded-full bg-sunset-500 px-5 py-2.5 text-sm font-bold text-white shadow-sm shadow-sunset-500/30 transition hover:-translate-y-0.5 hover:bg-sunset-600 hover:shadow-md"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            fill="currentColor"
            class="h-4 w-4"
          >
            <path d="M11.645 20.91 12 21l.355-.09C17.79 19.2 22 15.05 22 9.75 22 6.57 19.43 4 16.25 4A5.24 5.24 0 0 0 12 6.09 5.24 5.24 0 0 0 7.75 4C4.57 4 2 6.57 2 9.75c0 5.3 4.21 9.45 9.645 11.16Z" />
          </svg>
          Donate Now
        </NuxtLink>
      </nav>

      <!-- Mobile toggle -->
      <button
        type="button"
        class="inline-flex h-10 w-10 items-center justify-center rounded-lg text-brand-900 hover:bg-brand-50 lg:hidden"
        :aria-expanded="mobileOpen"
        aria-controls="mobile-menu"
        @click="mobileOpen = !mobileOpen"
      >
        <span class="sr-only">Toggle navigation</span>
        <svg v-if="!mobileOpen" class="h-6 w-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
        <svg v-else class="h-6 w-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
        </svg>
      </button>
    </div>

    <!-- Mobile menu -->
    <Transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 -translate-y-2"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div
        v-if="mobileOpen"
        id="mobile-menu"
        class="border-t border-brand-100/60 bg-white lg:hidden"
      >
        <div class="space-y-1 px-4 pb-4 pt-3">
          <NuxtLink
            v-for="link in navLinks"
            :key="link.to"
            :to="link.to"
            class="block rounded-lg px-3 py-2 text-base font-semibold text-brand-900/80 hover:bg-brand-50"
            active-class="bg-brand-50 text-brand-900"
          >
            {{ link.label }}
          </NuxtLink>
          <NuxtLink
            to="/donate"
            class="mt-2 flex items-center justify-center rounded-full bg-sunset-500 px-5 py-3 text-base font-bold text-white shadow-sm hover:bg-sunset-600"
          >
            Donate Now
          </NuxtLink>
        </div>
      </div>
    </Transition>
  </header>
</template>
