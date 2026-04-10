<script setup lang="ts">
/**
 * TournamentHero Component
 * Mobile-First Responsive version.
 */

defineProps<{
  title: string
  subtitle: string
  image: string
  dataAlt?: string
}>()
</script>

<template>
  <div class="relative py-12 sm:py-20 lg:py-28 mb-6 sm:mb-10 rounded-2xl overflow-hidden group border border-outline-variant/10 shadow-2xl flex items-center min-h-[280px] sm:min-h-[400px]">
    <!-- Background Gradient -->
    <div class="absolute inset-0 bg-gradient-to-r from-surface-container-low via-surface-container-low/90 sm:via-surface-container-low/80 to-transparent z-10"></div>
    
    <!-- Background Image -->
    <img 
      class="absolute inset-0 w-full h-full object-cover opacity-40 group-hover:scale-105 transition-transform duration-[2000ms] ease-out" 
      :data-alt="dataAlt" 
      :src="image"
      aria-hidden="true"
    />
    
    <!-- Content Container -->
    <div class="relative z-20 px-6 sm:px-10 lg:px-16 w-full">
      <h2 class="text-4xl sm:text-6xl lg:text-8xl font-headline font-bold tracking-tighter text-white mb-3 sm:mb-6 leading-[0.9] drop-shadow-[0_10px_20px_rgba(0,0,0,0.5)] max-w-4xl">
        {{ title }}
      </h2>
      <p class="text-primary sm:text-secondary tracking-[0.2em] sm:tracking-[0.4em] font-label uppercase text-[10px] sm:text-xs lg:text-sm font-black opacity-90 border-l-2 border-primary/50 pl-4 py-1">
        {{ subtitle }}
      </p>
    </div>
  </div>
</template>

<style scoped>
.font-headline {
  font-family: 'Space Grotesk', sans-serif;
}
.font-label {
  font-family: 'Inter', sans-serif;
}
</style>
