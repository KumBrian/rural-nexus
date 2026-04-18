<template>
  <header class="sticky top-0 z-50 glass-nav border-b no-border shadow-sm">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-20 items-center">
        <!-- Logo -->
        <div class="flex-shrink-0 flex items-center">
          <NuxtLink to="/" class="flex items-center gap-2 group">
            <div class="w-10 h-10 hex-mask bg-gradient-to-br from-cyan-500 to-leaf-500 flex items-center justify-center text-white font-bold text-xl transition-transform group-hover:scale-105">
              R
            </div>
            <span class="font-display font-bold text-xl text-primary-container tracking-tight">RuralNexus</span>
          </NuxtLink>
        </div>

        <!-- Navigation -->
        <nav class="hidden md:flex space-x-8">
          <NuxtLink to="/" class="text-on-surface hover:text-primary-container px-3 py-2 text-sm font-medium transition-colors">Home</NuxtLink>
          <NuxtLink to="/about" class="text-on-surface hover:text-primary-container px-3 py-2 text-sm font-medium transition-colors">Who We Are</NuxtLink>
          <NuxtLink to="/services" class="text-on-surface hover:text-primary-container px-3 py-2 text-sm font-medium transition-colors">Our Services</NuxtLink>
        </nav>

        <!-- CTA & Utility -->
        <div class="flex items-center">
          <!-- Fake Search Icon SVG -->
          <button class="p-2 text-on-surface-variant hover:text-primary-container rounded-full hidden md:block transition-colors">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line>
            </svg>
          </button>
          <div class="ml-4 flex gap-3">
            <NuxtLink to="/contact" class="hidden sm:inline-flex items-center justify-center px-5 py-2.5 border border-transparent text-sm font-medium rounded-md text-on-primary bg-primary hover:bg-primary-container ambient-shadow transition-all">
              Contact Us
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>
