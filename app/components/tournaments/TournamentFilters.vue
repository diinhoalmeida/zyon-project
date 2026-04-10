<script setup lang="ts">
/**
 * TournamentFilters Component
 * Mobile-First Responsive version.
 */

const gameOptions = ['Todos os Jogos', 'Hyperdrift Ultra', 'Neon Siege', 'Void Runner']
const prizeOptions = ['Qualquer Valor', '$0 - $500', '$500 - $2,500', '$2,500+']
const statusOptions = ['Ao Vivo e Futuros', 'Inscrições Abertas', 'Em Andamento', 'Finalizados']

const selectedGame = ref('Todos os Jogos')
const selectedPrize = ref('Qualquer Valor')
const selectedStatus = ref('Ao Vivo e Futuros')

function resetFilters() {
  selectedGame.value = 'Todos os Jogos'
  selectedPrize.value = 'Qualquer Valor'
  selectedStatus.value = 'Ao Vivo e Futuros'
}
</script>

<template>
  <div class="bg-surface-container-low border border-outline-variant/10 rounded-2xl p-5 sm:p-8 mb-6 sm:mb-10 shadow-xl backdrop-blur-sm">
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 items-end">
      
      <!-- Game Filter -->
      <div class="space-y-2">
        <label class="block text-[10px] uppercase tracking-[0.2em] text-slate-500 ml-1 font-bold">Série do Jogo</label>
        <div class="relative group">
          <select 
            v-model="selectedGame"
            class="w-full bg-surface-container-high border border-outline-variant/20 rounded-xl py-3.5 pl-4 pr-10 text-on-surface appearance-none focus:ring-2 focus:ring-primary/50 transition-all cursor-pointer outline-none text-sm group-hover:border-primary/30"
          >
            <option v-for="game in gameOptions" :key="game" :value="game">{{ game }}</option>
          </select>
          <span class="material-symbols-outlined absolute right-3 top-1/2 -translate-y-1/2 pointer-events-none text-slate-400 group-hover:text-primary transition-colors">expand_more</span>
        </div>
      </div>

      <!-- Prize Filter -->
      <div class="space-y-2">
        <label class="block text-[10px] uppercase tracking-[0.2em] text-slate-500 ml-1 font-bold">Premiação</label>
        <div class="relative group">
          <select 
            v-model="selectedPrize"
            class="w-full bg-surface-container-high border border-outline-variant/20 rounded-xl py-3.5 pl-4 pr-10 text-on-surface appearance-none focus:ring-2 focus:ring-primary/50 transition-all cursor-pointer outline-none text-sm group-hover:border-primary/30"
          >
            <option v-for="prize in prizeOptions" :key="prize" :value="prize">{{ prize }}</option>
          </select>
          <span class="material-symbols-outlined absolute right-3 top-1/2 -translate-y-1/2 pointer-events-none text-slate-400 group-hover:text-primary transition-colors">expand_more</span>
        </div>
      </div>

      <!-- Status Filter -->
      <div class="space-y-2">
        <label class="block text-[10px] uppercase tracking-[0.2em] text-slate-500 ml-1 font-bold">Status da Arena</label>
        <div class="relative group">
          <select 
            v-model="selectedStatus"
            class="w-full bg-surface-container-high border border-outline-variant/20 rounded-xl py-3.5 pl-4 pr-10 text-on-surface appearance-none focus:ring-2 focus:ring-primary/50 transition-all cursor-pointer outline-none text-sm group-hover:border-primary/30"
          >
            <option v-for="status in statusOptions" :key="status" :value="status">{{ status }}</option>
          </select>
          <span class="material-symbols-outlined absolute right-3 top-1/2 -translate-y-1/2 pointer-events-none text-slate-400 group-hover:text-primary transition-colors">expand_more</span>
        </div>
      </div>

      <!-- Reset Button -->
      <button 
        @click="resetFilters"
        class="w-full sm:w-auto bg-surface-container-highest hover:bg-surface-bright text-secondary px-8 py-3.5 rounded-xl flex items-center justify-center gap-2 transition-all font-bold border border-secondary/20 hover:border-secondary/50 active:scale-95 shadow-lg group"
      >
        <span class="material-symbols-outlined text-xl group-hover:rotate-180 transition-transform duration-500">filter_list</span>
        <span class="text-xs uppercase tracking-widest">Limpar Filtros</span>
      </button>
      
    </div>
  </div>
</template>
