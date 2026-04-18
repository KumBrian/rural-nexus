<script setup lang="ts">
useHead({ title: 'Impact — Horizon Aid' })
</script>

<template>
  <div>
    <section class="mx-auto max-w-4xl px-4 pt-24 sm:px-6 lg:px-8">
      <p class="text-sm font-bold uppercase tracking-wider text-brand-600">Our Impact</p>
      <h1 class="mt-3 text-4xl font-extrabold tracking-tight text-brand-900 sm:text-5xl">
        The numbers behind the mission.
      </h1>
      <p class="mt-6 text-lg leading-relaxed text-brand-900/70">
        We publish every outcome — the wins and the setbacks — in our open
        ledger. Below is a snapshot of our global footprint.
      </p>
    </section>

    <ImpactMetrics />
  </div>
</template>
