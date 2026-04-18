<script setup lang="ts">
const email = ref('')
const submitted = ref(false)

function handleSubscribe() {
  if (!email.value) return
  // Mock submission — wire to a real endpoint later.
  submitted.value = true
  email.value = ''
  setTimeout(() => (submitted.value = false), 4000)
}

const year = new Date().getFullYear()

const columns = [
  {
    title: 'Organization',
    links: ['About Us', 'Our Team', 'Careers', 'Annual Reports', 'Press'],
  },
  {
    title: 'Programs',
    links: ['Humanitarian Aid', 'Clean Water', 'Education', 'Climate Action', 'Emergency Relief'],
  },
  {
    title: 'Get Involved',
    links: ['Donate', 'Volunteer', 'Fundraise', 'Partnerships', 'Contact'],
  },
]
</script>

<template>
  <footer class="mt-24 bg-brand-900 text-brand-100">
    <div class="mx-auto max-w-7xl px-4 py-16 sm:px-6 lg:px-8">
      <div class="grid gap-12 lg:grid-cols-12">
        <!-- Brand + newsletter -->
        <div class="lg:col-span-5">
          <div class="flex items-center gap-3">
            <span class="flex h-11 w-11 items-center justify-center rounded-xl bg-gradient-to-br from-brand-500 to-leaf-400 text-white">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round" class="h-5 w-5">
                <path d="M12 21s-7-4.5-7-11a7 7 0 0 1 14 0c0 6.5-7 11-7 11Z" />
                <circle cx="12" cy="10" r="2.5" />
              </svg>
            </span>
            <div>
              <p class="text-xl font-bold text-white">Horizon Aid</p>
              <p class="text-xs uppercase tracking-wider text-brand-300">Since 2004</p>
            </div>
          </div>

          <p class="mt-5 max-w-md text-sm leading-relaxed text-brand-200">
            A global NGO delivering humanitarian and environmental relief to the communities that need it most. Every gift fuels real, measurable change on the ground.
          </p>

          <form class="mt-6 max-w-md" @submit.prevent="handleSubscribe">
            <label for="footer-newsletter" class="block text-sm font-semibold text-white">
              Stay in the loop
            </label>
            <p class="mt-1 text-xs text-brand-300">
              Monthly stories from the field. No spam, ever.
            </p>
            <div class="mt-3 flex flex-col gap-2 sm:flex-row">
              <input
                id="footer-newsletter"
                v-model="email"
                type="email"
                required
                placeholder="you@example.com"
                class="w-full flex-1 rounded-full border border-brand-700 bg-brand-800/80 px-5 py-3 text-sm text-white placeholder:text-brand-300 focus:border-leaf-400 focus:outline-none focus:ring-2 focus:ring-leaf-400/40"
              />
              <button
                type="submit"
                class="inline-flex items-center justify-center rounded-full bg-leaf-500 px-5 py-3 text-sm font-bold text-white transition hover:bg-leaf-600"
              >
                Subscribe
              </button>
            </div>
            <p
              v-if="submitted"
              class="mt-2 text-xs font-medium text-leaf-300"
            >
              ✓ Thanks for subscribing — check your inbox soon.
            </p>
          </form>
        </div>

        <!-- Link columns -->
        <div class="grid grid-cols-2 gap-8 sm:grid-cols-3 lg:col-span-7">
          <div v-for="col in columns" :key="col.title">
            <h3 class="text-sm font-bold uppercase tracking-wider text-white">
              {{ col.title }}
            </h3>
            <ul class="mt-4 space-y-3">
              <li v-for="link in col.links" :key="link">
                <a
                  href="#"
                  class="text-sm text-brand-200 transition hover:text-white"
                >{{ link }}</a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <div class="mt-14 flex flex-col items-start justify-between gap-6 border-t border-brand-800 pt-8 sm:flex-row sm:items-center">
        <p class="text-xs text-brand-300">
          © {{ year }} Horizon Aid. All rights reserved. Registered 501(c)(3) non-profit.
        </p>

        <!-- Social icons -->
        <div class="flex items-center gap-2">
          <a
            v-for="social in ['twitter', 'facebook', 'instagram', 'linkedin', 'youtube']"
            :key="social"
            href="#"
            :aria-label="social"
            class="flex h-9 w-9 items-center justify-center rounded-full bg-brand-800 text-brand-200 transition hover:bg-leaf-500 hover:text-white"
          >
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="h-4 w-4">
              <template v-if="social === 'twitter'">
                <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231 5.45-6.231Zm-1.161 17.52h1.833L7.084 4.126H5.117L17.083 19.77Z" />
              </template>
              <template v-else-if="social === 'facebook'">
                <path d="M22 12c0-5.52-4.48-10-10-10S2 6.48 2 12c0 4.84 3.44 8.87 8 9.8V15H8v-3h2V9.5A3.5 3.5 0 0 1 13.5 6H16v3h-2c-.55 0-1 .45-1 1v2h3v3h-3v6.95c5.05-.5 9-4.76 9-9.95Z" />
              </template>
              <template v-else-if="social === 'instagram'">
                <path d="M12 2.2c3.2 0 3.58.01 4.85.07 1.17.05 1.8.25 2.23.41.56.22.96.48 1.38.9.42.42.68.82.9 1.38.16.42.36 1.06.41 2.23.06 1.27.07 1.65.07 4.85s-.01 3.58-.07 4.85c-.05 1.17-.25 1.8-.41 2.23-.22.56-.48.96-.9 1.38-.42.42-.82.68-1.38.9-.42.16-1.06.36-2.23.41-1.27.06-1.65.07-4.85.07s-3.58-.01-4.85-.07c-1.17-.05-1.8-.25-2.23-.41a3.72 3.72 0 0 1-1.38-.9 3.72 3.72 0 0 1-.9-1.38c-.16-.42-.36-1.06-.41-2.23C2.21 15.58 2.2 15.2 2.2 12s.01-3.58.07-4.85c.05-1.17.25-1.8.41-2.23.22-.56.48-.96.9-1.38.42-.42.82-.68 1.38-.9.42-.16 1.06-.36 2.23-.41C8.42 2.21 8.8 2.2 12 2.2Zm0 1.8c-3.15 0-3.5.01-4.75.07-1.02.05-1.57.22-1.94.36-.48.19-.83.41-1.2.78-.37.37-.59.72-.78 1.2-.14.37-.31.92-.36 1.94-.06 1.25-.07 1.6-.07 4.75s.01 3.5.07 4.75c.05 1.02.22 1.57.36 1.94.19.48.41.83.78 1.2.37.37.72.59 1.2.78.37.14.92.31 1.94.36 1.25.06 1.6.07 4.75.07s3.5-.01 4.75-.07c1.02-.05 1.57-.22 1.94-.36.48-.19.83-.41 1.2-.78.37-.37.59-.72.78-1.2.14-.37.31-.92.36-1.94.06-1.25.07-1.6.07-4.75s-.01-3.5-.07-4.75c-.05-1.02-.22-1.57-.36-1.94a3.22 3.22 0 0 0-.78-1.2 3.22 3.22 0 0 0-1.2-.78c-.37-.14-.92-.31-1.94-.36-1.25-.06-1.6-.07-4.75-.07Zm0 3.07a4.93 4.93 0 1 1 0 9.86 4.93 4.93 0 0 1 0-9.86Zm0 8.13a3.2 3.2 0 1 0 0-6.4 3.2 3.2 0 0 0 0 6.4Zm6.28-8.34a1.15 1.15 0 1 1-2.3 0 1.15 1.15 0 0 1 2.3 0Z" />
              </template>
              <template v-else-if="social === 'linkedin'">
                <path d="M20.45 20.45h-3.55v-5.57c0-1.33-.03-3.04-1.85-3.04-1.85 0-2.13 1.45-2.13 2.94v5.67H9.36V9h3.41v1.56h.05c.48-.9 1.64-1.85 3.38-1.85 3.62 0 4.29 2.38 4.29 5.48v6.26ZM5.34 7.43a2.06 2.06 0 1 1 0-4.12 2.06 2.06 0 0 1 0 4.12ZM7.12 20.45H3.56V9h3.56v11.45Z" />
              </template>
              <template v-else>
                <path d="M23.5 6.2a3.02 3.02 0 0 0-2.13-2.14C19.5 3.55 12 3.55 12 3.55s-7.5 0-9.37.51A3.02 3.02 0 0 0 .5 6.2C0 8.07 0 12 0 12s0 3.93.5 5.8a3.02 3.02 0 0 0 2.13 2.14c1.87.51 9.37.51 9.37.51s7.5 0 9.37-.51a3.02 3.02 0 0 0 2.13-2.14C24 15.93 24 12 24 12s0-3.93-.5-5.8ZM9.6 15.6V8.4l6.24 3.6-6.24 3.6Z" />
              </template>
            </svg>
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>
