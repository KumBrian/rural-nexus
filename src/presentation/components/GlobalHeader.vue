<script setup lang="ts">
import { ref } from 'vue';
import { Menu, X, Search, ChevronRight } from 'lucide-vue-next';

const isMenuOpen = ref(false);

const navLinks = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Programs', path: '/programs' },
  { name: 'Services', path: '/services' },
  { name: 'Volunteer', path: '/volunteer' },
  { name: 'Events', path: '/events' },
  { name: 'Gallery', path: '/gallery' },
];

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value;
  // Prevent scrolling when menu is open
  if (typeof document !== 'undefined') {
    document.body.style.overflow = isMenuOpen.value ? 'hidden' : '';
  }
}

function closeMenu() {
  isMenuOpen.value = false;
  if (typeof document !== 'undefined') {
    document.body.style.overflow = '';
  }
}
</script>

<template>
  <header class="sticky top-0 z-50 glass-nav border-b no-border shadow-sm">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-20 items-center">
        <!-- Logo -->
        <div class="flex-shrink-0 flex items-center relative z-50">
          <NuxtLink to="/" @click="closeMenu" class="flex items-center gap-2 group">
            <div class="w-10 h-10 hex-mask bg-gradient-to-br from-cyan-500 to-leaf-500 flex items-center justify-center text-white font-bold text-xl transition-transform group-hover:scale-105">
              R
            </div>
            <span class="font-display font-bold text-xl text-primary-container tracking-tight">RuralNexus</span>
          </NuxtLink>
        </div>

        <!-- Desktop Navigation -->
        <nav class="hidden lg:flex space-x-6 items-center">
          <NuxtLink 
            v-for="link in navLinks" 
            :key="link.path"
            :to="link.path"
            class="text-on-surface/80 hover:text-primary-container px-2 py-2 text-sm font-medium transition-colors"
            active-class="text-primary font-bold"
          >
            {{ link.name }}
          </NuxtLink>
        </nav>

        <!-- Right Actions -->
        <div class="flex items-center relative z-50">
          <!-- Search -->
          <button class="p-2 text-on-surface-variant hover:text-primary-container rounded-full hidden md:block transition-colors">
            <Search class="w-5 h-5" />
          </button>
          
          <!-- Contact CTA -->
          <div class="ml-4 hidden sm:block">
            <NuxtLink to="/contact" @click="closeMenu" class="inline-flex items-center justify-center px-5 py-2.5 border border-transparent text-sm font-medium rounded-xl text-on-primary bg-primary hover:bg-primary-container ambient-shadow transition-all">
              Contact Us
            </NuxtLink>
          </div>

          <!-- Mobile Menu Toggle -->
          <button 
            @click="toggleMenu"
            class="ml-4 p-2 text-on-surface hover:text-primary transition-colors lg:hidden rounded-lg hover:bg-surface-container-low"
            aria-label="Toggle menu"
          >
            <component :is="isMenuOpen ? X : Menu" class="w-6 h-6" />
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Menu Drawer (Side Slide) -->
    <Transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="translate-x-full"
      enter-to-class="translate-x-0"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="translate-x-0"
      leave-to-class="translate-x-full"
    >
      <div 
        v-if="isMenuOpen" 
        class="fixed inset-y-0 right-0 w-full max-w-sm bg-white/95 backdrop-blur-xl shadow-2xl z-40 lg:hidden border-l border-outline-variant/10"
      >
        <div class="flex flex-col h-full pt-28 pb-10 px-6">
          <!-- Mobile Nav Links -->
          <nav class="flex-grow flex flex-col gap-2">
            <NuxtLink 
              v-for="link in navLinks" 
              :key="link.path"
              :to="link.path"
              @click="closeMenu"
              class="flex items-center justify-between px-6 py-4 rounded-2xl text-lg font-display font-bold text-on-surface hover:bg-primary/5 hover:text-primary transition-all group"
              active-class="bg-primary/5 text-primary"
            >
              {{ link.name }}
              <ChevronRight class="w-5 h-5 opacity-0 group-hover:opacity-100 transition-all -translate-x-2 group-hover:translate-x-0" />
            </NuxtLink>
          </nav>

          <!-- Mobile Footer CTA -->
          <div class="mt-auto px-6 pt-6 border-t border-outline-variant/10">
            <NuxtLink 
              to="/contact" 
              @click="closeMenu"
              class="flex items-center justify-center w-full py-4 bg-primary text-white rounded-2xl font-bold shadow-xl shadow-primary/20 hover:bg-primary-container transition-all"
            >
              Contact Us
            </NuxtLink>
          </div>
        </div>
      </div>
    </Transition>

    <!-- Overlay Backdrop -->
    <Transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div 
        v-if="isMenuOpen" 
        @click="closeMenu"
        class="fixed inset-0 bg-primary/20 backdrop-blur-sm z-30 lg:hidden"
      ></div>
    </Transition>
  </header>
</template>

<style scoped>
.glass-nav {
  background: rgba(248, 250, 248, 0.85);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
}

.hex-mask {
  clip-path: polygon(25% 0%, 75% 0%, 100% 50%, 75% 100%, 25% 100%, 0% 50%);
}

.no-border {
  border-bottom: none !important;
}
</style>
