<template>
  <div class="flex flex-col min-h-screen bg-surface text-on-surface">
    <!-- Header -->
    <section class="py-20 bg-surface-container-low">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <h1 class="text-4xl md:text-5xl font-display font-bold mb-6">Research & Resources</h1>
        <p class="text-lg md:text-xl text-on-surface-variant max-w-3xl font-body">
          Open access to our methodologies, whitepapers, and transdisciplinary tools built for agronomic resilience.
        </p>
      </div>
    </section>

    <!-- Table/Grid Area -->
    <section class="py-16 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex-grow w-full">
      
      <!-- Toolbar -->
      <div class="flex flex-col sm:flex-row justify-between items-center mb-8 gap-4">
        <!-- Search -->
        <div class="relative w-full sm:w-96">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="absolute left-3 top-1/2 -translate-y-1/2 text-on-surface-variant"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
          <input 
            v-model="searchQuery" 
            type="text" 
            placeholder="Search papers, tools, keywords..." 
            class="w-full pl-10 pr-4 py-2 border border-outline-variant bg-surface-container-lowest rounded-lg focus:outline-none focus:ring-2 focus:ring-primary focus:border-transparent transition-all"
          >
        </div>

        <!-- Filter -->
        <div class="flex gap-2 w-full sm:w-auto overflow-x-auto pb-2 sm:pb-0 hide-scrollbar">
          <button 
            v-for="cat in ['All', 'Publication', 'Workshop', 'Policy']" 
            :key="cat"
            @click="activeCategory = cat"
            class="px-4 py-1.5 rounded-full text-sm font-semibold transition-all whitespace-nowrap"
            :class="activeCategory === cat ? 'bg-primary text-white' : 'bg-surface-container-low text-on-surface hover:bg-surface-container-high'"
          >
            {{ cat }}
          </button>
        </div>
      </div>

      <!-- Results Grid -->
      <div v-if="filteredResources.length > 0" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div 
          v-for="doc in filteredResources" 
          :key="doc.id"
          class="bg-surface-container-lowest border border-outline-variant rounded-xl p-6 hover:shadow-lg transition-shadow flex flex-col h-full"
        >
          <div class="flex justify-between items-start mb-4">
            <span class="px-2.5 py-1 bg-cyan/10 text-cyan text-xs font-bold uppercase tracking-wider rounded">
              {{ doc.category }}
            </span>
            <span class="text-xs text-on-surface-variant font-medium">{{ doc.date }}</span>
          </div>
          <h3 class="font-display font-bold text-xl mb-2 text-on-surface group-hover:text-primary transition-colors">
            <NuxtLink :to="`/news/${doc.id}`" class="hover:underline">{{ doc.title }}</NuxtLink>
          </h3>
          <p class="font-body text-sm text-on-surface-variant mb-6 flex-grow line-clamp-3">
            {{ doc.summary }}
          </p>
          <div class="pt-4 border-t border-outline-variant mt-auto flex justify-between items-center">
            <NuxtLink :to="`/news/${doc.id}`" class="text-primary font-semibold text-sm hover:text-primary-container flex items-center gap-1">
              Read Abstract
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
            </NuxtLink>
            <button class="text-on-surface-variant hover:text-cyan transition-colors" title="Download PDF">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
            </button>
          </div>
        </div>
      </div>
      
      <!-- Empty State -->
      <div v-else class="text-center py-20 bg-surface-container-lowest rounded-xl border border-outline-variant border-dashed">
        <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" class="mx-auto text-on-surface-variant mb-4 opacity-50"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
        <p class="text-lg font-medium text-on-surface-variant">No resources match your filters.</p>
        <button @click="searchQuery = ''; activeCategory = 'All'" class="mt-4 text-cyan hover:underline font-medium">Clear all filters</button>
      </div>

    </section>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
import { useAsyncData } from '#imports';
import { MockNewsEventRepository } from '@infrastructure/repositories/MockNewsEventRepository';

// In a real app we might have a separate DocumentRepository, but for the mockup we'll piggy-back on NewsEvents categorizations.
const repo = new MockNewsEventRepository();
const { data: allResources } = await useAsyncData('researchData', () => repo.getLatestEvents(20));

const searchQuery = ref('');
const activeCategory = ref('All');

const filteredResources = computed(() => {
  if (!allResources.value) return [];
  
  return allResources.value.filter(doc => {
    const matchesSearch = doc.title.toLowerCase().includes(searchQuery.value.toLowerCase()) || 
                          doc.summary.toLowerCase().includes(searchQuery.value.toLowerCase());
    const matchesCategory = activeCategory.value === 'All' || doc.category === activeCategory.value;
    
    return matchesSearch && matchesCategory;
  });
});
</script>

<style scoped>
.hide-scrollbar::-webkit-scrollbar {
  display: none;
}
.hide-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
</style>
