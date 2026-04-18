<template>
  <div class="flex flex-col">
    <section class="py-20 bg-primary-container text-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center relative z-10">
        <h1 class="text-4xl md:text-5xl font-display font-bold mb-6">Our Services & Program Areas</h1>
        <p class="text-lg md:text-xl opacity-90 max-w-3xl mx-auto font-body">
          RuralNexus operates through five strategic pillars, providing the structural glue needed for multi-stakeholder and transdisciplinary approaches.
        </p>
      </div>
    </section>

    <section class="py-24 bg-surface text-on-surface">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
          <div 
            v-for="(area, index) in homeData?.programAreas" 
            :key="area.id"
            class="flex flex-col md:flex-row gap-8 bg-surface-container-low p-8 rounded-xl ambient-shadow hover:-translate-y-2 transition-transform duration-300"
          >
            <div 
              class="flex-shrink-0 w-24 h-24 hex-mask text-white flex items-center justify-center font-bold text-3xl"
              :class="getColorClass(area.colorTheme)"
            >
              {{ area.code }}
            </div>
            <div>
              <h3 class="text-2xl font-display font-bold mb-4">{{ area.title }}</h3>
              <p class="text-on-surface-variant font-body leading-relaxed mb-6">
                {{ area.description }}
              </p>
              
              <!-- SDG Mapping -->
              <div class="mb-6">
                <p class="text-xs font-bold text-on-surface-variant uppercase tracking-widest mb-2">Targeted Goals</p>
                <div class="flex flex-wrap gap-2">
                  <span 
                    v-for="sdg in area.sdgs" 
                    :key="sdg.code"
                    class="px-2.5 py-1 text-xs font-bold text-white rounded shadow-sm"
                    :style="{ backgroundColor: sdg.color }"
                  >
                    {{ sdg.code }}: {{ sdg.title }}
                  </span>
                </div>
              </div>

              <!-- Core Initiatives -->
              <div class="mb-8">
                 <p class="text-xs font-bold text-on-surface-variant uppercase tracking-widest mb-3">Core Initiatives</p>
                 <ul class="space-y-3">
                   <li v-for="init in area.initiatives" :key="init.title" class="flex gap-2 items-start">
                     <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-cyan mt-1 flex-shrink-0"><polyline points="20 6 9 17 4 12"/></svg>
                     <div>
                       <strong class="font-display text-sm text-on-surface block">{{ init.title }}</strong>
                       <span class="text-xs text-on-surface-variant font-body">{{ init.desc }}</span>
                     </div>
                   </li>
                 </ul>
              </div>

              <NuxtLink to="/contact" class="inline-flex items-center gap-2 text-primary font-bold text-sm tracking-wide uppercase hover:text-primary-container transition-colors group">
                Inquire about collaboration
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="group-hover:translate-x-1 transition-transform"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
              </NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { useAsyncData } from '#imports';
import { GetHomeDataUseCase } from '@application/use_cases/GetHomeDataUseCase';
import { MockProgramAreaRepository } from '@infrastructure/repositories/MockProgramAreaRepository';
import { MockNewsEventRepository } from '@infrastructure/repositories/MockNewsEventRepository';
import { MockTeamRepository } from '@infrastructure/repositories/MockTeamRepository';

const useCase = new GetHomeDataUseCase(
  new MockProgramAreaRepository(),
  new MockNewsEventRepository(),
  new MockTeamRepository()
);

const { data: homeData } = await useAsyncData('servicesData', () => useCase.execute());

function getColorClass(theme: string) {
  const map: Record<string, string> = {
    cyan: 'bg-cyan',
    primary: 'bg-primary-container',
    navy: 'bg-navy',
    amber: 'bg-amber',
    leaf: 'bg-leaf',
  };
  return map[theme] || 'bg-primary-container';
}
</script>
