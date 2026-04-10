<script setup lang="ts">
/**
 * DetailsHero Component
 * Hero section for the Tournament Details page.
 */

defineProps<{
  title: string
  game: string
  image: string
  prizePool: string
  status: string
  statusClass: string
  organizerName: string
  organizerLogo: string
  participants: number
  maxParticipants: number
  feeReal?: string
  feeZyon?: string
}>()

const emit = defineEmits<{
  (e: 'join-click'): void
}>()
</script>

<template>
  <div class="relative py-12 sm:py-20 lg:py-24 mb-6 sm:mb-10 rounded-3xl overflow-hidden group border border-outline-variant/10 shadow-2xl flex flex-col justify-end min-h-[350px] sm:min-h-[450px]">
    <!-- Background Gradient -->
    <div class="absolute inset-0 bg-linear-to-t from-surface-container-highest via-surface-container-low/80 to-transparent z-10 w-full h-full"></div>
    
    <!-- Background Image -->
    <img 
      class="absolute inset-0 w-full h-full object-cover opacity-50 group-hover:scale-105 transition-transform duration-2000 ease-out" 
      :src="image"
      :alt="title"
      aria-hidden="true"
    />
    
    <!-- Top Organizer Tag -->
    <div class="absolute top-6 left-6 z-20 flex items-center gap-3 bg-surface/60 backdrop-blur-md border border-outline-variant/20 py-2 px-4 rounded-full">
      <img :src="organizerLogo" alt="Organizer Logo" class="w-6 h-6 rounded-full object-cover border border-outline-variant/30" />
      <span class="text-xs font-bold text-white uppercase tracking-widest">Organizado por: <span class="text-primary">{{ organizerName }}</span></span>
    </div>

    <!-- Status Badge (Top Right) -->
    <div class="absolute top-6 right-6 z-20">
      <span 
        class="px-4 py-2 text-[10px] sm:text-xs font-bold uppercase tracking-[0.2em] rounded-full border shadow-lg backdrop-blur-md"
        :class="statusClass"
      >
        {{ status }}
      </span>
    </div>

    <!-- Content Container -->
    <div class="relative z-20 px-6 sm:px-10 lg:px-16 w-full flex flex-col sm:flex-row items-end justify-between gap-6 pb-6 mt-auto">
      <div class="w-full sm:w-auto">
        <div class="flex items-center gap-2 mb-2 sm:mb-4">
          <p class="text-white/80 tracking-[0.2em] sm:tracking-[0.3em] font-label uppercase text-[10px] sm:text-xs font-bold border-l-2 border-primary pl-3 py-0.5">
            {{ game }}
          </p>
        </div>
        <h1 class="text-3xl sm:text-5xl lg:text-7xl font-headline font-bold tracking-tighter text-white mb-2 leading-[1.1] drop-shadow-xl">
          {{ title }}
        </h1>
        
        <div class="flex items-center gap-6 mt-4">
          <div class="flex items-center gap-2 text-white">
            <span class="material-symbols-outlined text-primary text-xl">group</span>
            <div class="flex flex-col">
              <span class="text-[9px] uppercase tracking-widest text-slate-400 font-bold leading-none mb-1">Inscritos</span>
              <span class="text-sm sm:text-base font-bold leading-none">{{ participants }} <span class="text-white/50">/</span> {{ maxParticipants }}</span>
            </div>
          </div>
          
          <div class="w-px h-8 bg-outline-variant/20 hidden sm:block"></div>
          
          <div class="flex items-center gap-2 text-white">
            <span class="material-symbols-outlined text-primary text-xl">account_balance_wallet</span>
            <div class="flex flex-col">
              <span class="text-[9px] uppercase tracking-widest text-slate-400 font-bold leading-none mb-1">Inscrição</span>
              <div class="flex items-center gap-2">
                <span class="text-sm font-bold leading-none text-green-400">{{ feeReal }}</span>
                <span class="text-[9px] text-slate-500 font-bold uppercase">ou</span>
                <span class="text-sm font-bold leading-none text-primary">{{ feeZyon }} ZC</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Action & Prize Area -->
      <div class="w-full sm:w-auto flex flex-col items-start sm:items-end gap-4 shrink-0 bg-surface-container/40 p-4 rounded-2xl border border-outline-variant/10 backdrop-blur-sm sm:bg-transparent sm:border-none sm:p-0">
        <div class="flex flex-col items-start sm:items-end">
          <span class="text-[10px] uppercase tracking-[0.3em] text-slate-300 font-bold mb-1">Premiação Estimada</span>
          <div class="flex items-center gap-2">
            <span class="material-symbols-outlined text-primary text-3xl sm:text-4xl" style="font-variation-settings: 'FILL' 1;">monetization_on</span>
            <span class="text-3xl sm:text-5xl font-headline font-bold text-primary tracking-tight drop-shadow-[0_0_15px_rgba(201,191,255,0.4)]">
              {{ prizePool }}
            </span>
          </div>
        </div>
        
        <button 
          @click="emit('join-click')"
          class="w-full sm:w-auto px-10 sm:px-14 py-3.5 sm:py-4 bg-linear-to-br from-primary to-primary-container text-on-primary rounded-xl font-bold text-xs sm:text-sm uppercase tracking-[0.2em] shadow-[0_0_20px_rgba(201,191,255,0.3)] hover:shadow-[0_0_30px_rgba(201,191,255,0.5)] hover:scale-105 active:scale-95 transition-all outline-none flex items-center justify-center gap-2 mt-2"
        >
          Entrar Agora
          <span class="material-symbols-outlined text-sm font-bold">arrow_forward</span>
        </button>
      </div>
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
