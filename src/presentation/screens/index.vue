<template>
  <div class="flex flex-col">
    <!-- Hero Section -->
    <section class="relative min-h-[85vh] flex items-center justify-center bg-primary-container overflow-hidden">
      <!-- Background Graphic Overlay simulating nature/agriculture placeholder -->
      <div class="absolute inset-0 z-0 opacity-20">
        <img src="https://images.unsplash.com/photo-1500382017468-9049fed747ef?ixlib=rb-4.0.3&auto=format&fit=crop&w=2560&q=80" alt="Agriculture Background" class="w-full h-full object-cover mix-blend-overlay" />
      </div>

      <!-- Geometric overlays -->
      <div class="absolute top-1/4 left-10 w-64 h-64 border-4 border-leaf/30 rounded-lg transform rotate-12 pointer-events-none animate-floaty"></div>
      <div class="absolute bottom-1/4 right-10 w-96 h-96 hex-mask bg-cyan/10 pointer-events-none"></div>

      <!-- Hero Content -->
      <div class="relative z-10 max-w-5xl mx-auto px-4 sm:px-6 lg:px-8 text-center text-white">
        <div class="mb-4 flex flex-wrap justify-center gap-2 text-xs uppercase tracking-wider font-semibold text-leaf animate-floaty">
          <span>Action Research</span> • 
          <span>Innovation</span> • 
          <span>Development</span> • 
          <span>Farming Systems</span>
        </div>
        <h1 class="font-display font-bold text-5xl md:text-7xl leading-tight mb-8">
          Empowering <br/><span class="text-transparent bg-clip-text bg-gradient-to-r from-leaf to-cyan">Rural Resilience</span>
        </h1>
        <p class="font-body text-lg md:text-xl text-surface-dim max-w-2xl mx-auto mb-10">
          Advancing UN Sustainable Development Goals to build resilient food systems through transdisciplinary research and strategic consultancy.
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <NuxtLink to="/services" class="px-8 py-4 bg-gradient-to-r from-primary to-primary-container text-white rounded-lg font-semibold hover:shadow-lg hover:shadow-leaf/20 transition-all">
            Explore Our Programs
          </NuxtLink>
          <NuxtLink to="/about" class="px-8 py-4 border border-outline-variant/30 text-white rounded-lg font-semibold hover:bg-white/5 transition-colors">
            Who We Are
          </NuxtLink>
        </div>
      </div>
    </section>

    <!-- The Hub: Program Areas -->
    <section class="py-24 bg-surface text-on-surface">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="mb-16 md:flex md:justify-between md:items-end">
          <div>
            <h2 class="font-display font-bold text-4xl mb-4">The Hub</h2>
            <p class="text-on-surface-variant font-body max-w-2xl">
              Our core strategic pillars are interconnected nodes functioning as a complete action research network.
            </p>
          </div>
          <NuxtLink to="/services" class="hidden md:inline-flex mt-4 items-center gap-2 text-primary font-bold hover:text-primary-container transition-colors">
            View All Services
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
          </NuxtLink>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <HexCard 
            v-for="area in homeData?.programAreas" 
            :key="area.id"
            :title="area.title"
            :description="area.description"
            :colorTheme="area.colorTheme"
          />
        </div>
      </div>
    </section>

    <!-- Success Stories & Testimonials -->
    <section class="py-24 bg-surface-container-low">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <h2 class="font-display font-bold text-4xl mb-12">"They say about us"</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="i in 3" :key="i" class="p-8 bg-surface rounded-lg ambient-shadow text-left">
            <svg class="h-8 w-8 text-amber mb-6 opacity-50" fill="currentColor" viewBox="0 0 24 24"><path d="M14.017 21v-7.391c0-5.704 3.731-9.57 8.983-10.609l.995 2.151c-2.432.917-3.995 3.638-3.995 5.849h4v10h-9.983zm-14.017 0v-7.391c0-5.704 3.748-9.57 9-10.609l.996 2.151c-2.433.917-3.996 3.638-3.996 5.849h3.983v10h-9.983z"/></svg>
            <p class="font-body text-on-surface-variant italic mb-6">"RuralNexus provided the structural glue needed to transition our local farming initiative into an internationally funded project. Their transdisciplinary methodology is unmatched."</p>
            <div>
              <p class="font-bold text-on-surface">Dr. Placeholder Name</p>
              <p class="text-sm border-t border-outline-variant pt-2 mt-2 text-primary-fixed-variant">Director, Agritech Cooperative {{i}}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- News & Highlights -->
    <section class="py-24 bg-surface relative overflow-hidden">
      <!-- Watermark -->
      <div class="absolute -left-32 top-0 w-[500px] h-[500px] hex-mask bg-surface-container-highest opacity-50 pointer-events-none"></div>

      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <h2 class="font-display font-bold text-4xl mb-12">Latest Insights & Reports</h2>
        
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-12">
          <!-- Left Col: Latest News -->
          <div class="lg:col-span-7 flex flex-col gap-4">
            <NewsCard 
              v-for="event in homeData?.latestEvents" 
              :key="event.id" 
              :event="event" 
            />
          </div>

          <!-- Right Col: Highlights -->
          <div class="lg:col-span-5 flex flex-col gap-6">
            <div 
              v-for="highlight in homeData?.highlightEvents" 
              :key="highlight.id"
              class="p-8 rounded-xl bg-gradient-to-br from-primary-container to-primary text-white ambient-shadow relative overflow-hidden group"
            >
              <div class="absolute -right-10 -top-10 w-32 h-32 hex-mask bg-white/10 group-hover:scale-110 transition-transform"></div>
              <span class="inline-block px-3 py-1 bg-amber text-on-tertiary-container text-xs font-bold uppercase tracking-wide rounded-full mb-4">
                {{ highlight.highlightCategory }}
              </span>
              <h3 class="font-display font-bold text-2xl mb-2">{{ highlight.title }}</h3>
              <p class="opacity-80 font-body">{{ highlight.summary }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Mission & SDGs -->
    <section class="py-24 bg-navy text-white relative overflow-hidden">
      <!-- Decoratives -->
      <div class="absolute -right-20 top-20 w-64 h-64 hex-mask bg-cyan/10 animate-floaty"></div>
      
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
        <div>
          <h2 class="font-display font-bold text-4xl mb-6">Aligned with the Global Goals</h2>
          <p class="font-body text-lg opacity-80 mb-8 leading-relaxed">
            Every programmatic area within our operational hub is strictly mapped to the United Nations Sustainable Development Goals. We don't just talk about sustainability; we build actionable frameworks that deliver measurable impact across the most vulnerable rural regions.
          </p>
          <NuxtLink to="/research" class="inline-flex items-center gap-2 border-b-2 border-leaf pb-1 font-bold hover:text-leaf transition-colors text-lg">
            Read our 2026 Impact Report &rarr;
          </NuxtLink>
        </div>

        <div class="grid grid-cols-2 sm:grid-cols-3 gap-4">
          <!-- SDG Blocks -->
          <div class="aspect-square bg-[#E5243B] p-4 flex flex-col justify-between hover:-translate-y-1 transition-transform cursor-default">
            <span class="font-bold text-xl">1</span>
            <span class="font-display font-bold text-sm uppercase leading-tight">No Poverty</span>
          </div>
          <div class="aspect-square bg-[#DDA63A] p-4 flex flex-col justify-between hover:-translate-y-1 transition-transform cursor-default">
            <span class="font-bold text-xl">2</span>
            <span class="font-display font-bold text-sm uppercase leading-tight">Zero Hunger</span>
          </div>
          <div class="aspect-square bg-[#4C9F38] p-4 flex flex-col justify-between hover:-translate-y-1 transition-transform cursor-default">
            <span class="font-bold text-xl">3</span>
            <span class="font-display font-bold text-sm uppercase leading-tight">Good Health</span>
          </div>
          <div class="aspect-square bg-[#C5192D] p-4 flex flex-col justify-between hover:-translate-y-1 transition-transform cursor-default">
            <span class="font-bold text-xl">4</span>
            <span class="font-display font-bold text-sm uppercase leading-tight">Quality Education</span>
          </div>
          <div class="aspect-square bg-[#3F7E44] p-4 flex flex-col justify-between hover:-translate-y-1 transition-transform cursor-default">
            <span class="font-bold text-xl">13</span>
            <span class="font-display font-bold text-sm uppercase leading-tight">Climate Action</span>
          </div>
          <div class="aspect-square bg-[#56C02B] p-4 flex flex-col justify-between hover:-translate-y-1 transition-transform cursor-default">
            <span class="font-bold text-xl">15</span>
            <span class="font-display font-bold text-sm uppercase leading-tight">Life on Land</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Network / Partners -->
    <section class="py-16 bg-surface-container-lowest border-t border-b border-surface-variant">
      <div class="max-w-7xl mx-auto px-4 text-center overflow-hidden">
        <p class="text-xs font-bold text-on-surface-variant uppercase tracking-widest mb-10">Collaborating with global leaders & research institutions</p>
        
        <div class="flex animate-[pulse_4s_ease-in-out_infinite] gap-12 sm:gap-24 opacity-50 grayscale justify-center flex-wrap">
          <div class="font-display font-black text-2xl flex items-center gap-2"><div class="w-6 h-6 bg-current rounded-full"></div> EcoAgri EU</div>
          <div class="font-display font-bold text-2xl tracking-tighter">GLOBAL HORIZON</div>
          <div class="font-display font-light text-2xl italic tracking-wider">Hohenheim Institute</div>
          <div class="font-display font-extrabold text-2xl uppercase">UN FAO Data</div>
          <div class="font-display font-bold text-2xl flex items-center gap-2 text-primary">AgroNexus</div>
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

// Setup dependencies (Normally via DI container)
const paRepo = new MockProgramAreaRepository();
const newsRepo = new MockNewsEventRepository();
const teamRepo = new MockTeamRepository();
const useCase = new GetHomeDataUseCase(paRepo, newsRepo, teamRepo);

const { data: homeData } = await useAsyncData('homeData', () => useCase.execute());
</script>
