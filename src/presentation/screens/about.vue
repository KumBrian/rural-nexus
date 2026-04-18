<template>
  <div class="flex flex-col min-h-screen">
    <!-- Header -->
    <section class="py-24 bg-surface-container-low text-on-surface relative overflow-hidden">
      <!-- Background Graphic -->
      <div class="absolute top-0 right-0 w-1/3 h-full hex-mask bg-primary opacity-5 -mr-24 -mt-12"></div>
      
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <p class="text-sm font-bold uppercase tracking-widest text-primary mb-4">Our Leadership</p>
        <h1 class="text-4xl md:text-5xl lg:text-6xl font-display font-bold mb-8 leading-tight tracking-tight">
          Who We Are
        </h1>
        <p class="text-lg md:text-xl text-on-surface-variant max-w-3xl font-body leading-relaxed">
          RuralNexus is an international network of researchers, agronomists, and project managers dedicated to empowering rural resilience through evidence-based innovation.
        </p>
      </div>
    </section>

    <!-- Organigram Section -->
    <section class="py-24 bg-surface text-on-surface">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="mb-16 flex flex-col md:flex-row md:items-end justify-between gap-6">
          <div class="max-w-2xl">
            <h2 class="text-3xl font-display font-bold mb-4">Organizational Structure</h2>
            <p class="text-on-surface-variant font-body">
              Our decentralized structure ensures that research remains grounded in field realities while maintaining rigorous international standards.
            </p>
          </div>
          <div class="flex gap-3">
            <button 
              @click="expandAll" 
              class="px-4 py-2 text-xs font-bold text-primary border border-primary/20 rounded-lg hover:bg-primary/5 transition-all text-nowrap"
            >
              Expand All
            </button>
            <button 
              @click="collapseAll" 
              class="px-4 py-2 text-xs font-bold text-on-surface-variant bg-surface-container-low rounded-lg hover:bg-surface-container-high transition-all text-nowrap"
            >
              Collapse All
            </button>
          </div>
        </div>
        
        <!-- Interactive Tree Container -->
        <div class="bg-surface-container-low/30 rounded-3xl p-8 lg:p-12 overflow-x-auto ambient-shadow border border-outline-variant/10">
          <div class="min-w-fit flex justify-center py-10">
            <template v-if="roots.length > 0">
              <OrgChartTree
                v-for="root in roots"
                :key="root.id"
                :node="mapToViewNode(root)"
                :children="getChildren(root.id)"
                :children-of="getChildren"
                :selected-id="selectedMemberId"
                :loading-depth="() => false"
                @select="handleSelect"
                @toggle="handleToggle"
              />
            </template>
            <div v-else class="flex py-20 items-center justify-center text-on-surface-variant opacity-50 font-body">
              <p>Loading organizational data...</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Detailed Info (Visible when a member is selected) -->
    <Transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="opacity-0 translate-y-10"
      enter-to-class="opacity-100 translate-y-0"
    >
      <section v-if="selectedMember" class="pb-24 bg-surface">
        <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="bg-primary-container text-on-primary-fixed rounded-3xl p-8 md:p-12 relative overflow-hidden group">
            <div class="absolute -right-12 -bottom-12 w-64 h-64 hex-mask bg-leaf opacity-20 pointer-events-none group-hover:scale-110 transition-transform duration-700"></div>
            
            <div class="relative z-10">
              <h3 class="text-3xl font-display font-bold mb-2">{{ selectedMember.name }}</h3>
              <p class="text-leaf-300 font-bold tracking-widest text-xs uppercase mb-8">{{ selectedMember.role }}</p>
              
              <div class="grid md:grid-cols-2 gap-12">
                <div>
                  <h4 class="text-sm font-bold opacity-60 uppercase mb-4 tracking-wider">Background</h4>
                  <p class="font-body text-lg leading-relaxed opacity-90">{{ selectedMember.bio || 'Detailed biography pending.' }}</p>
                </div>
                <div>
                  <h4 class="text-sm font-bold opacity-60 uppercase mb-4 tracking-wider">Expertise</h4>
                  <div class="flex flex-wrap gap-2">
                    <span 
                      v-for="exp in selectedMember.expertise || ['Sustainable Development']" 
                      :key="exp"
                      class="px-3 py-1.5 bg-white/10 rounded-lg text-sm font-medium border border-white/10"
                    >
                      {{ exp }}
                    </span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </Transition>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';
import { useAsyncData } from '#imports';
import { MockTeamRepository } from '@infrastructure/repositories/MockTeamRepository';
import OrgChartTree from '../components/OrgChartTree.vue';

const teamRepo = new MockTeamRepository();
const { data: allMembers } = await useAsyncData('teamData', () => teamRepo.getOrganigram());

const expandedIds = ref(new Set<string>(['dir1', 'pac3', 'pac4']));
const selectedMemberId = ref<string | null>(null);

const roots = computed(() => {
  if (!allMembers.value) return [];
  return allMembers.value.filter(m => m.parentId === null);
});

const selectedMember = computed(() => {
  if (!allMembers.value || !selectedMemberId.value) return null;
  return allMembers.value.find(m => m.id === selectedMemberId.value) || null;
});

function getChildren(parentId: string) {
  if (!allMembers.value) return [];
  return allMembers.value.filter(m => m.parentId === parentId).map(m => mapToViewNode(m));
}

function handleToggle(id: string) {
  if (expandedIds.value.has(id)) {
    expandedIds.value.delete(id);
  } else {
    expandedIds.value.add(id);
  }
}

function handleSelect(id: string) {
  selectedMemberId.value = selectedMemberId.value === id ? null : id;
}

function expandAll() {
  if (!allMembers.value) return;
  allMembers.value.forEach(m => expandedIds.value.add(m.id));
}

function collapseAll() {
  expandedIds.value.clear();
}

function mapToViewNode(member: any) {
  // Determine depth (simplified for this view)
  const getDepth = (id: string, current = 0): number => {
    const m = allMembers.value?.find(item => item.id === id);
    if (!m || !m.parentId) return current;
    return getDepth(m.parentId, current + 1);
  };

  const subordinateCount = allMembers.value?.filter(m => m.parentId === member.id).length || 0;

  // Determine category and status based on role or hierarchy
  let category = 'Operations';
  let statusColor: 'active' | 'field' | 'research' | 'advisory' = 'active';

  if (member.role === 'Director') {
    category = 'Directorate';
    statusColor = 'active';
  } else if (member.role.includes('Advisory')) {
    category = 'Advisory Board';
    statusColor = 'advisory';
  } else if (member.role.startsWith('PAC')) {
    category = 'Program Mgmt';
    statusColor = 'active';
  } else if (member.role.includes('Lead') || member.role.includes('Tech')) {
    category = 'Research';
    statusColor = 'field';
  }

  return {
    ...member,
    subordinateCount,
    isExpanded: expandedIds.value.has(member.id),
    depth: getDepth(member.id),
    category,
    statusColor,
    statusLabel: statusColor.charAt(0).toUpperCase() + statusColor.slice(1)
  };
}
</script>
