<template>
  <div class="flex flex-col">
    <!-- Header -->
    <section class="py-20 bg-surface-container-low text-on-surface">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <h1 class="text-4xl md:text-5xl font-display font-bold mb-6">Who We Are</h1>
        <p class="text-lg md:text-xl text-on-surface-variant max-w-3xl font-body">
          We are an international network of researchers, agronomists, and project managers dedicated to empowering rural resilience.
        </p>
      </div>
    </section>

    <!-- Organigram -->
    <section class="py-24 bg-surface text-on-surface">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <h2 class="text-3xl font-display font-bold mb-12">Organisational Structure</h2>
        
        <div class="bg-surface-container-low rounded-xl p-8 overflow-x-auto ambient-shadow">
          <!-- Simplified hierarchical tree visualization -->
          <div class="min-w-[800px] flex flex-col items-center">
            
            <!-- Level 1: Director -->
            <div v-for="node in organigram" :key="node.id" class="flex flex-col items-center w-full">
              <OrganigramNode :node="node" color="bg-primary-container" />
              
              <div v-if="node.children && node.children.length > 0" class="w-full mt-8 relative">
                <!-- Connecting lines -->
                <div class="absolute top-0 left-1/2 -ml-px w-px h-8 bg-outline-variant"></div>
                <div class="absolute top-8 left-1/4 right-1/4 h-px bg-outline-variant"></div>

                <!-- Next Level -->
                <div class="flex justify-between mt-8 relative z-10 w-full px-12">
                  <div v-for="child in node.children" :key="child.id" class="flex flex-col items-center">
                    <OrganigramNode :node="child" :color="child.role === 'Advisory' ? 'bg-amber' : 'bg-leaf'" />
                    
                    <div v-if="child.children && child.children.length > 0" class="flex flex-col items-center mt-8 relative">
                      <div class="absolute -top-8 left-1/2 -ml-px w-px h-8 bg-outline-variant"></div>
                      <div v-for="grandchild in child.children" :key="grandchild.id" class="mt-4">
                        <OrganigramNode :node="grandchild" color="bg-cyan" />
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>

          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import { useAsyncData } from '#imports';
import { GetOrganigramUseCase } from '@application/use_cases/GetOrganigramUseCase';
import { MockTeamRepository } from '@infrastructure/repositories/MockTeamRepository';
import OrganigramNode from '../components/OrganigramNode.vue';

const useCase = new GetOrganigramUseCase(new MockTeamRepository());
const { data: organigram } = await useAsyncData('organigramData', () => useCase.execute());
</script>
