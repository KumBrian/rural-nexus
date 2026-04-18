<script setup lang="ts">
import { useAsyncData } from '#imports';
import { GetHomeDataUseCase } from '@application/use_cases/GetHomeDataUseCase';
import { MockProgramAreaRepository } from '@infrastructure/repositories/MockProgramAreaRepository';
import { MockNewsEventRepository } from '@infrastructure/repositories/MockNewsEventRepository';
import { MockTeamRepository } from '@infrastructure/repositories/MockTeamRepository';
import { Check, ArrowRight } from 'lucide-vue-next';

useHead({ title: 'Advisory & Operations — RuralNexus' });

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
    navy: 'bg-primary',
    amber: 'bg-amber',
    leaf: 'bg-leaf',
  };
  return map[theme] || 'bg-primary-container';
}
</script>

<template>
  <div class="flex flex-col min-h-screen">
    <!-- Restored & Refined Header -->
    <section class="py-24 bg-surface-container-low text-on-surface relative overflow-hidden">
      <div class="absolute top-0 right-0 w-1/3 h-full hex-mask bg-primary opacity-5 -mr-24 -mt-12"></div>
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <p class="text-xs font-bold uppercase tracking-[0.3em] text-primary mb-6">Our Operations</p>
        <h1 class="text-4xl md:text-5xl lg:text-6xl font-display font-bold mb-8 leading-tight tracking-tight">
          Services & <span class="text-leaf-600 italic">Program Areas</span>
        </h1>
        <p class="text-lg md:text-xl text-on-surface-variant max-w-3xl font-body leading-relaxed opacity-80">
          RuralNexus operates through five strategic pillars, providing the structural glue needed for multi-stakeholder and transdisciplinary approaches.
        </p>
      </div>
    </section>

    <!-- Content Grid (Restored Data) -->
    <section class="py-24 bg-surface text-on-surface">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
          <div 
            v-for="area in homeData?.programAreas" 
            :key="area.id"
            class="flex flex-col md:flex-row gap-8 bg-surface-container-low p-8 rounded-[40px] hover:bg-surface-container-lowest transition-all duration-500 hover:-translate-y-2 group"
          >
            <!-- Hexagonal Icon / Code -->
            <div 
              class="flex-shrink-0 w-24 h-24 hex-mask text-white flex items-center justify-center font-display font-bold text-3xl transition-transform group-hover:scale-105"
              :class="getColorClass(area.colorTheme)"
            >
              {{ area.code }}
            </div>

            <div class="flex-grow">
              <h3 class="text-2xl font-display font-bold mb-4 group-hover:text-primary transition-colors">{{ area.title }}</h3>
              <p class="text-on-surface-variant font-body leading-relaxed mb-8 opacity-80">
                {{ area.description }}
              </p>
              
              <!-- SDG Mapping (Vibrant Badges) -->
              <div class="mb-8">
                <p class="text-[10px] font-bold text-on-surface-variant uppercase tracking-widest mb-3 opacity-60">Strategic Alignment (SDGs)</p>
                <div class="flex flex-wrap gap-2">
                  <span 
                    v-for="sdg in area.sdgs" 
                    :key="sdg.code"
                    class="px-3 py-1 text-[10px] font-bold text-white rounded-lg shadow-sm"
                    :style="{ backgroundColor: sdg.color }"
                  >
                    Goal {{ sdg.code }}
                  </span>
                </div>
              </div>

              <!-- Core Initiatives (Restored with Lucide) -->
              <div class="mb-10 p-6 bg-surface-container-lowest rounded-3xl border border-outline-variant/10">
                 <p class="text-[10px] font-bold text-on-surface-variant uppercase tracking-widest mb-6 opacity-60">Active Field Initiatives</p>
                 <ul class="space-y-4">
                   <li v-for="init in area.initiatives" :key="init.title" class="flex gap-4 items-start">
                     <div class="mt-1 flex-shrink-0 w-5 h-5 rounded-full bg-primary/10 flex items-center justify-center text-primary">
                       <Check class="w-3 h-3" />
                     </div>
                     <div>
                       <strong class="font-display text-sm text-on-surface block mb-1">{{ init.title }}</strong>
                       <span class="text-xs text-on-surface-variant font-body opacity-80 leading-relaxed">{{ init.desc }}</span>
                     </div>
                   </li>
                 </ul>
              </div>

              <NuxtLink to="/contact" class="inline-flex items-center gap-3 text-primary font-bold text-xs tracking-[0.2em] uppercase hover:text-primary-container transition-all group/link">
                Inquire about collaboration
                <ArrowRight class="w-4 h-4 transition-transform group-hover/link:translate-x-1" />
              </NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
// Already defined above
</script>

<style scoped>
.hex-mask {
  clip-path: polygon(25% 0%, 75% 0%, 100% 50%, 75% 100%, 25% 100%, 0% 50%);
}
</style>
