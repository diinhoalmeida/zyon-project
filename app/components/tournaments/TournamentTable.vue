<script setup lang="ts">
/**
 * TournamentTable Component
 * Mobile-First Responsive version.
 * Displays as a list of cards on mobile and a structured table on desktop.
 */

interface Tournament {
  name: string
  game: string
  prize: string
  participants: number
  maxParticipants: number
  status: string
  statusClass: string
  image: string
  canJoin: boolean
  progress: number
  // New fields
  type: 'best_of_2' | 'best_of_3' | 'best_of_5' | 'play_2'
  typeName: string
  startTime: string
  endTime: string
  matchesPlayed: number
  totalMatchesNeeded: number
  feeReal?: string
  feeZyon?: string
  id?: string
}

defineProps<{
  tournaments: Tournament[]
}>()

const emit = defineEmits<{
  (e: 'join', tournament: Tournament): void
}>()

const getRulesText = (type: Tournament['type']) => {
  switch (type) {
    case 'best_of_2': return 'Contabiliza suas 2 melhores partidas no período.'
    case 'best_of_3': return 'Contabiliza suas 3 melhores partidas no período.'
    case 'best_of_5': return 'Contabiliza suas 5 melhores partidas no período.'
    case 'play_2': return 'Contabiliza as 2 primeiras partidas após sua inscrição.'
    default: return ''
  }
}
</script>

<template>
  <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
    <div 
      v-for="tournament in tournaments" 
      :key="tournament.name"
      @click="$router.push('/tournaments/' + (tournament.id || 'cyber-strike-elite'))"
      class="bg-[#12141D] border border-white/5 rounded-[24px] overflow-hidden flex flex-col hover:-translate-y-1 hover:shadow-2xl hover:shadow-primary/10 hover:border-primary/30 transition-all duration-300 cursor-pointer group"
    >
      <!-- Top Image Area -->
      <div class="relative h-[180px] w-full bg-surface-container-highest overflow-hidden">
        <img 
          class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700 ease-out opacity-80 group-hover:opacity-100" 
          :src="tournament.image" 
          :alt="tournament.name"
        />
        
        <!-- Timer / Status Badge -->
        <div class="absolute top-4 left-4 bg-black/60 backdrop-blur-md px-3 py-1.5 rounded-full flex items-center gap-2 border border-white/10">
          <span class="material-symbols-outlined text-[12px] text-white">schedule</span>
          <span class="text-[10px] font-bold text-white tracking-wider">{{ new Date(tournament.startTime).toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }) }}</span>
        </div>

        <!-- Tag Badge (Right) -->
        <div class="absolute top-4 right-4 bg-primary/20 backdrop-blur-md px-2 py-1 rounded border border-primary/30 flex items-center gap-1.5">
          <span class="w-1.5 h-1.5 rounded-full bg-primary animate-pulse"></span>
          <span class="text-[9px] font-bold text-primary uppercase tracking-widest">{{ tournament.game }}</span>
        </div>
      </div>

      <!-- Content Area -->
      <div class="p-5 flex-1 flex flex-col bg-linear-to-b from-[#1E2333]/40 to-transparent">
        
        <!-- Date Subtitle -->
        <div class="text-[10px] text-slate-400 font-bold uppercase tracking-widest mb-1">
          {{ new Date(tournament.startTime).toLocaleDateString('en-US', { weekday: 'short', day: 'numeric', month: 'short' }) }}, {{ new Date(tournament.startTime).toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }) }}
        </div>
        
        <!-- Title -->
        <h3 class="text-lg font-headline font-bold text-white leading-tight mb-2 group-hover:text-primary transition-colors line-clamp-1">
          {{ tournament.name }}
        </h3>
        
        <!-- Description / Rules excerpt -->
        <p class="text-xs text-slate-400 mb-5 line-clamp-2 leading-relaxed">
          {{ getRulesText(tournament.type) }} <span v-if="tournament.feeReal">Inscrição: {{ tournament.feeReal }} / {{ tournament.feeZyon }}.</span>
        </p>
        
        <!-- Actions Row (Prize + Join) -->
        <div class="flex items-center gap-3 mt-auto">
          <!-- Prize Pill (Yellowish/Primary based on image) -->
          <div class="bg-[#FFD43B] text-black px-4 py-2.5 rounded-xl font-black flex items-center justify-center gap-1 min-w-[110px] shadow-[0_0_15px_rgba(255,212,59,0.2)]">
            <span class="text-sm tracking-tight">{{ tournament.prize }}</span>
          </div>
          
          <!-- Join Button -->
          <button 
            v-if="tournament.canJoin"
            @click.stop="emit('join', tournament)"
            class="flex-1 bg-[#2C344A] hover:bg-[#3D4763] text-white border border-white/5 py-2.5 rounded-xl text-xs font-bold uppercase tracking-wider text-center transition-colors"
          >
            Join Tournament
          </button>
          <button 
            v-else
            class="flex-1 bg-surface-container-highest text-slate-500 py-2.5 rounded-xl text-xs font-bold uppercase tracking-wider text-center cursor-not-allowed opacity-60"
          >
            Lotado
          </button>
        </div>

        <!-- Footer: Slots & Avatars -->
        <div class="mt-5 flex items-center justify-between">
          
          <!-- Mock Avatar Group -->
          <div class="flex -space-x-2">
            <img class="w-6 h-6 rounded-full border-2 border-[#12141D] bg-surface-container-high" src="https://i.pravatar.cc/100?u=12" alt="Participant 1"/>
            <img class="w-6 h-6 rounded-full border-2 border-[#12141D] bg-surface-container-high" src="https://i.pravatar.cc/100?u=13" alt="Participant 2"/>
            <img class="w-6 h-6 rounded-full border-2 border-[#12141D] bg-surface-container-high" src="https://i.pravatar.cc/100?u=14" alt="Participant 3"/>
            <div class="w-6 h-6 rounded-full border-2 border-[#12141D] bg-[#2C344A] flex items-center justify-center">
              <span class="text-[8px] font-bold text-white">+{{ tournament.participants > 3 ? tournament.participants - 3 : 0 }}</span>
            </div>
          </div>

          <!-- Slots count -->
          <div class="flex items-center gap-1.5">
            <span class="w-3 h-3 rounded-full border-2 border-primary/30 flex items-center justify-center">
              <span class="w-1.5 h-1.5 rounded-full bg-primary/70"></span>
            </span>
            <span class="text-[10px] font-bold text-slate-400">{{ tournament.participants }}/{{ tournament.maxParticipants }} Slots</span>
          </div>

        </div>
        
      </div>
    </div>
  </div>
</template>

<style scoped>
.font-headline {
  font-family: 'Space Grotesk', sans-serif;
}
</style>
