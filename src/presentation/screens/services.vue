<script setup lang="ts">
import { Settings, Shield, Zap, Target } from 'lucide-vue-next';

useHead({ title: 'Advisory Services — RuralNexus' });

const services = [
  {
    title: 'Policy Advisory',
    description: 'Developing resilient governance frameworks for rural districts undergoing climate transition.',
    icon: Shield
  },
  {
    title: 'Precision Agronomics',
    description: 'Satellite-integrated soil health monitoring and adaptive crop rotation planning.',
    icon: Target
  },
  {
    title: 'Infrastructural Design',
    description: 'Off-grid water, energy, and connectivity nodes designed for extreme rural environments.',
    icon: Zap
  },
  {
    title: 'Strategic Implementation',
    description: 'End-to-end management of large-scale development projects from concept to field hub.',
    icon: Settings
  }
];
</script>

<template>
  <div class="flex flex-col min-h-screen">
    <!-- Hero Header -->
    <section class="py-24 bg-surface-container-low text-on-surface relative overflow-hidden">
      <div class="absolute top-0 right-0 w-1/3 h-full hex-mask bg-primary opacity-5 -mr-24 -mt-12"></div>
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <p class="text-xs font-bold uppercase tracking-[0.3em] text-primary mb-6">Expert Solutions</p>
        <h1 class="text-4xl md:text-5xl lg:text-6xl font-display font-bold mb-8 leading-tight tracking-tight">
          Advisory & <span class="text-leaf-600 italic">Field Operations</span>
        </h1>
        <p class="text-lg md:text-xl text-on-surface-variant max-w-3xl font-body leading-relaxed opacity-80">
          Scaling rural resilience through engineering excellence, policy innovation, and rigorous field implementation.
        </p>
      </div>
    </section>

    <!-- Services Grid -->
    <section class="py-24 bg-surface">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div 
            v-for="service in services" 
            :key="service.title"
            class="p-8 rounded-3xl bg-surface-container-low hover:bg-surface-container-lowest transition-all duration-500 hover:-translate-y-2 group"
          >
            <div class="w-12 h-12 hex-mask bg-primary/5 flex items-center justify-center text-primary mb-8 group-hover:bg-primary group-hover:text-white transition-all">
              <component :is="service.icon" class="w-6 h-6" />
            </div>
            <h3 class="text-lg font-display font-bold mb-4">{{ service.title }}</h3>
            <p class="text-sm text-on-surface-variant font-body leading-relaxed opacity-70 group-hover:opacity-100 transition-opacity">
              {{ service.description }}
            </p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.hex-mask {
  clip-path: polygon(25% 0%, 75% 0%, 100% 50%, 75% 100%, 25% 100%, 0% 50%);
}
</style>
