<script setup lang="ts">
import { 
  Droplets, 
  Sprout, 
  ShieldAlert, 
  BookOpen, 
  Tractor, 
  Heart, 
  ArrowRight,
  Target,
  Globe,
  Zap
} from 'lucide-vue-next';

useHead({ title: 'Strategic Programs — RuralNexus' });

const programs = [
  {
    title: 'Water Governance & Sovereignty',
    description:
      'Implementing decentralized, solar-powered filtration systems and community-led watershed management protocols in arid innovation zones.',
    stat: '312 systems',
    statLabel: 'Deployed Innovation Nodes',
    icon: Droplets,
    color: 'emerald'
  },
  {
    title: 'Regenerative Agro-Systems',
    description:
      'Advancing native-species reforestation and soil health monitoring through satellite data integration and local knowledge mapping.',
    stat: '1.2M nodes',
    statLabel: 'Active Reforestation Points',
    icon: Sprout,
    color: 'leaf'
  },
  {
    title: 'Climate Resilience Hubs',
    description:
      'Establishing rapid-response field stations and climate-adaptive infrastructure for vulnerable agrarian communities across the Global South.',
    stat: '48 hubs',
    statLabel: 'Active Regional Stations',
    icon: ShieldAlert,
    color: 'amber'
  },
  {
    title: 'Action Research Education',
    description:
      'Scaling field-based learning modules and scholarships for the next generation of rural development leaders and agronomists.',
    stat: '9,400 leaders',
    statLabel: 'Empowered Research Fellows',
    icon: BookOpen,
    color: 'cyan'
  },
  {
    title: 'Sustainable Food Nexuses',
    description:
      'Developing drought-resistant seed registries and circular economy grain banks co-managed with regional cooperatives.',
    stat: '22,000 cooperatives',
    statLabel: 'Networked Field Partners',
    icon: Tractor,
    color: 'primary'
  },
  {
    title: 'Biosocial Health Integration',
    description:
      'Merging clinical rural health services with nutritional security data to improve community resilience metrics.',
    stat: '14 hubs',
    statLabel: 'Integrated Health Stations',
    icon: Heart,
    color: 'leaf-dark'
  },
];
</script>

<template>
  <div class="flex flex-col min-h-screen bg-surface">
    <!-- Hero Section -->
    <header class="relative pt-32 pb-40 overflow-hidden bg-primary text-white">
      <!-- Organic Motifs -->
      <div class="absolute inset-0 opacity-10 pointer-events-none">
        <div class="absolute -right-24 -top-24 w-96 h-96 hex-mask bg-white"></div>
        <div class="absolute right-48 top-48 w-64 h-64 hex-mask bg-leaf"></div>
        <div class="absolute left-10 bottom-10 w-80 h-80 hex-mask border-2 border-white/20"></div>
      </div>
      
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <div class="max-w-3xl">
          <p class="text-xs font-bold uppercase tracking-[0.3em] text-leaf-300 mb-6 flex items-center gap-3">
            <Target class="w-4 h-4" /> Strategic Impact
          </p>
          <h1 class="text-4xl md:text-5xl lg:text-7xl font-display font-bold mb-8 leading-[1.1] tracking-tight">
            Design for <span class="text-leaf-300 italic">Resilience.</span>
          </h1>
          <p class="text-lg md:text-xl font-body text-white/80 leading-relaxed balance py-4">
            Our strategic programs are not mere interventions; they are evidence-based frameworks designed to scale rural autonomy and ecological health through shared innovation.
          </p>
          
          <div class="flex flex-wrap gap-8 mt-12 pt-12 border-t border-white/10">
             <div class="flex items-center gap-3">
               <Globe class="w-5 h-5 text-leaf-300" />
               <span class="text-sm font-bold tracking-widest uppercase">Global Network</span>
             </div>
             <div class="flex items-center gap-3">
               <Zap class="w-5 h-5 text-leaf-300" />
               <span class="text-sm font-bold tracking-widest uppercase">Immediate Action</span>
             </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Content Grid -->
    <section class="relative -mt-24 pb-24 z-20">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <article 
            v-for="program in programs" 
            :key="program.title"
            class="group bg-surface-container-lowest p-8 rounded-[40px] shadow-sm hover:shadow-2xl transition-all duration-500 hover:-translate-y-2 flex flex-col"
          >
            <!-- Icon & Category -->
            <div class="flex items-start justify-between mb-10">
              <div class="w-16 h-16 hex-mask bg-surface-container-low flex items-center justify-center p-0.5">
                <div class="w-full h-full hex-mask bg-primary/5 group-hover:bg-primary transition-colors flex items-center justify-center text-primary group-hover:text-white">
                  <component :is="program.icon" class="w-7 h-7" />
                </div>
              </div>
              <div class="h-[1px] flex-grow bg-outline-variant/10 mx-4 mt-8"></div>
            </div>

            <!-- Content -->
            <h3 class="text-xl font-display font-bold text-on-surface mb-4 group-hover:text-primary transition-colors">
              {{ program.title }}
            </h3>
            <p class="text-sm font-body text-on-surface-variant leading-relaxed opacity-80 mb-10 flex-grow">
              {{ program.description }}
            </p>

            <!-- Stats Bar -->
            <div class="bg-surface-container-low rounded-3xl p-5 border border-outline-variant/5">
              <p class="text-2xl font-display font-bold text-tertiary mb-1">
                {{ program.stat }}
              </p>
              <p class="text-[10px] font-bold text-on-surface-variant uppercase tracking-widest opacity-60">
                {{ program.statLabel }}
              </p>
            </div>
            
            <button class="mt-8 flex items-center gap-2 text-xs font-bold text-primary opacity-0 group-hover:opacity-100 transition-all -translate-x-4 group-hover:translate-x-0">
              LEARN MORE <ArrowRight class="w-4 h-4" />
            </button>
          </article>
        </div>
      </div>
    </section>

    <!-- Partners / Collaboration Section (Replaces Donate) -->
    <section class="py-24 bg-surface-container-low relative overflow-hidden">
       <div class="absolute left-0 top-0 w-64 h-64 hex-mask bg-primary opacity-5 -ml-32 -mt-32"></div>
       
       <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 text-center">
         <h2 class="text-3xl md:text-4xl font-display font-bold text-on-surface mb-6">
           Join the RuralNexus Ecosystem
         </h2>
         <p class="text-lg text-on-surface-variant font-body mb-12 max-w-2xl mx-auto opacity-80 leading-relaxed">
           Our programs scale through collaborative intelligence. We are seeking academic partners, field organizations, and technology hub collaborators.
         </p>
         <div class="flex flex-wrap justify-center gap-4">
           <button class="px-8 py-4 bg-primary text-white rounded-xl font-bold hover:bg-primary-container transition-all shadow-xl shadow-primary/20">
             Research Partnership
           </button>
           <button class="px-8 py-4 bg-surface-container-highest text-on-surface rounded-xl font-bold hover:bg-surface-container-high transition-all">
             Regional Collaboration
           </button>
         </div>
       </div>
    </section>
  </div>
</template>

<style scoped>
.hex-mask {
  clip-path: polygon(25% 0%, 75% 0%, 100% 50%, 75% 100%, 25% 100%, 0% 50%);
}

.balance {
  text-wrap: balance;
}
</style>
