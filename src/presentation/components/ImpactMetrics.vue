<script setup lang="ts">
interface Metric {
  value: number
  suffix: string
  label: string
  description: string
  icon: 'people' | 'projects' | 'shield'
}

const metrics: Metric[] = [
  {
    value: 10000,
    suffix: '+',
    label: 'Lives Impacted',
    description: 'Direct beneficiaries reached across 34 countries since 2004.',
    icon: 'people',
  },
  {
    value: 50,
    suffix: '+',
    label: 'Active Projects',
    description: 'Long-term initiatives running on 4 continents right now.',
    icon: 'projects',
  },
  {
    value: 100,
    suffix: '%',
    label: 'Transparency',
    description: 'Every dollar is traced from donor to field in our public ledger.',
    icon: 'shield',
  },
]

// Animated count-up. Starts when the section enters the viewport.
const displayed = ref<number[]>(metrics.map(() => 0))
const sectionRef = ref<HTMLElement | null>(null)
const animated = ref(false)

function animateCounts() {
  if (animated.value) return
  animated.value = true

  const duration = 1600
  const start = performance.now()

  function tick(now: number) {
    const progress = Math.min((now - start) / duration, 1)
    // easeOutCubic
    const eased = 1 - Math.pow(1 - progress, 3)
    displayed.value = metrics.map(m => Math.round(m.value * eased))
    if (progress < 1) requestAnimationFrame(tick)
  }

  requestAnimationFrame(tick)
}

onMounted(() => {
  if (!sectionRef.value || typeof IntersectionObserver === 'undefined') {
    animateCounts()
    return
  }
  const observer = new IntersectionObserver(
    (entries) => {
      for (const entry of entries) {
        if (entry.isIntersecting) {
          animateCounts()
          observer.disconnect()
          break
        }
      }
    },
    { threshold: 0.35 },
  )
  observer.observe(sectionRef.value)
})

function formatNumber(n: number) {
  return n.toLocaleString('en-US')
}
</script>

<template>
  <section ref="sectionRef" class="relative bg-white py-20 sm:py-28">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="mx-auto max-w-2xl text-center">
        <p class="text-sm font-bold uppercase tracking-wider text-brand-600">
          Our Impact
        </p>
        <h2 class="mt-3 text-3xl font-extrabold tracking-tight text-brand-900 sm:text-4xl">
          Measurable change, verified in the open.
        </h2>
        <p class="mt-4 text-lg text-brand-900/70">
          We publish every outcome — the wins and the setbacks — because trust
          is earned with receipts, not promises.
        </p>
      </div>

      <div class="mt-14 grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
        <div
          v-for="(metric, i) in metrics"
          :key="metric.label"
          class="group relative overflow-hidden rounded-3xl border border-brand-100 bg-gradient-to-br from-white to-brand-50/60 p-8 shadow-sm transition hover:-translate-y-1 hover:shadow-lg"
        >
          <div class="absolute -right-6 -top-6 h-28 w-28 rounded-full bg-leaf-100/60 blur-2xl transition group-hover:bg-leaf-200/80" />

          <span class="relative flex h-12 w-12 items-center justify-center rounded-2xl bg-brand-600 text-white shadow-sm">
            <svg v-if="metric.icon === 'people'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-6 w-6">
              <path stroke-linecap="round" stroke-linejoin="round" d="M17 20v-2a4 4 0 0 0-4-4H7a4 4 0 0 0-4 4v2M10 12a4 4 0 1 0 0-8 4 4 0 0 0 0 8Zm11 8v-2a4 4 0 0 0-3-3.87M16 4.13a4 4 0 0 1 0 7.75" />
            </svg>
            <svg v-else-if="metric.icon === 'projects'" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-6 w-6">
              <path stroke-linecap="round" stroke-linejoin="round" d="M3 9.5 12 3l9 6.5V21a1 1 0 0 1-1 1h-5v-6H9v6H4a1 1 0 0 1-1-1V9.5Z" />
            </svg>
            <svg v-else xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="h-6 w-6">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10Z" />
              <path stroke-linecap="round" stroke-linejoin="round" d="m9 12 2 2 4-4" />
            </svg>
          </span>

          <p class="relative mt-6 text-5xl font-extrabold tracking-tight text-brand-900 sm:text-6xl">
            {{ formatNumber(displayed[i] ?? 0) }}<span class="text-leaf-500">{{ metric.suffix }}</span>
          </p>
          <p class="relative mt-2 text-lg font-bold text-brand-900">
            {{ metric.label }}
          </p>
          <p class="relative mt-2 text-sm leading-relaxed text-brand-900/70">
            {{ metric.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
