<script setup lang="ts">
import { ref } from 'vue'
// Sidebar state shared with Header via useState composable
const isSidebarOpen = useState('adminSidebarOpen', () => false)
const route = useRoute()

function closeSidebar() {
  isSidebarOpen.value = false
}

// Game icons for the far-left mini-bar
const games = [
  { id: 'lol', img: 'https://logo.clearbit.com/leagueoflegends.com', selected: true },
  { id: 'val', img: 'https://logo.clearbit.com/playvalorant.com', selected: false },
  { id: 'cs2', img: 'https://logo.clearbit.com/counter-strike.net', selected: false }
]

const navigationItems = [
  { label: 'Início', icon: 'home', to: '/home' },
  { label: 'Torneios', icon: 'emoji_events', to: '/tournaments', badge: '12' },
  { label: 'Carteira', icon: 'account_balance_wallet', to: '/wallet' },
  { label: 'Estatísticas', icon: 'leaderboard', to: '/statistics' }
]

const configureItems = [
  { label: 'Suporte', icon: 'support_agent', to: '#' },
  { label: 'Admin', icon: 'admin_panel_settings', to: '/admin-central' },
]

function isActive(to: string) {
  return route.path === to
}
</script>

<template>
  <!-- Mobile Backdrop Overlay -->
  <Transition name="fade">
    <div 
      v-if="isSidebarOpen" 
      class="fixed inset-0 z-40 bg-black/60 backdrop-blur-sm lg:hidden"
      @click="closeSidebar"
    />
  </Transition>

  <!-- Sidebar Drawer: Dual Pane -->
  <aside 
    :class="[
      'fixed left-0 top-[72px] h-[calc(100vh-72px)] w-[280px] z-50 bg-[#10102e]/95 backdrop-blur-xl flex font-[\'Space_Grotesk\'] tracking-wider',
      'transition-transform duration-300 ease-[cubic-bezier(0.4,0,0.2,1)]',
      'border-r border-outline-variant/10 lg:border-r-0 shadow-[20px_0_40px_rgba(0,0,0,0.3)]',
      isSidebarOpen ? 'translate-x-0' : '-translate-x-full lg:translate-x-0'
    ]"
  >
    <!-- Pane 1: Mini Bar (Games) -->
    <div class="w-16 shrink-0 bg-background/50 flex flex-col items-center py-4 border-r border-outline-variant/10">

      <!-- Game List -->
      <div class="flex-1 flex flex-col items-center gap-3 w-full overflow-y-auto no-scrollbar py-2">
        <div 
          v-for="game in games" 
          :key="game.id"
          class="w-10 h-10 rounded-xl overflow-hidden cursor-pointer transition-all relative group"
          :class="game.selected ? 'ring-2 ring-primary ring-offset-2 ring-offset-[#0A0B10]' : 'hover:ring-2 hover:ring-slate-600 ring-offset-2 ring-offset-[#0A0B10]'"
        >
          <img 
            :src="game.img" 
            class="w-full h-full object-cover transition-opacity" 
            :class="game.selected ? 'opacity-100 bg-[#12141D]' : 'opacity-40 grayscale group-hover:opacity-60 bg-[#12141D]'"
            crossorigin="anonymous"
          />
          <div v-if="game.selected" class="absolute -left-1 top-1/2 -translate-y-1/2 w-1.5 h-6 bg-primary rounded-r-lg"></div>
        </div>
        
        <button class="w-10 h-10 rounded-xl border border-white/10 flex items-center justify-center text-slate-500 hover:text-white hover:bg-white/5 transition-all outline-none">
          <span class="material-symbols-outlined">add</span>
        </button>
      </div>

      <!-- Bottom System Icons -->
      <div class="mt-auto flex flex-col items-center gap-4 pt-4">
        <button class="text-slate-500 hover:text-primary transition-colors outline-none pb-2">
          <span class="material-symbols-outlined text-[20px]">help</span>
        </button>
      </div>
    </div>

    <!-- Pane 2: Main Navigation -->
    <div class="flex-1 flex flex-col overflow-hidden py-4">
      
      <!-- Close button for mobile -->
      <button 
        class="absolute top-4 right-4 p-2 rounded-full text-slate-400 hover:text-white hover:bg-surface-container-high transition-all lg:hidden"
        @click="closeSidebar"
      >
        <span class="material-symbols-outlined">close</span>
      </button>

      <!-- Profile Section -->
      <div class="px-5 mb-6">
        <div class="flex items-center gap-3">
          <div class="relative shrink-0">
            <img src="https://i.pravatar.cc/150?u=zyon" class="w-10 h-10 rounded-full border border-primary object-cover shadow-sm bg-surface-container-highest" />
            <div class="absolute -bottom-1 -right-1 w-3.5 h-3.5 bg-primary rounded-full text-black flex items-center justify-center text-[8px] font-black border-2 border-[#10102e]">2</div>
          </div>
          <div class="min-w-0">
            <p class="text-[9px] text-slate-400 font-bold uppercase tracking-widest truncate">Bom dia,</p>
            <h2 class="text-[13px] font-black text-white uppercase tracking-wider truncate mt-0.5">Player 1</h2>
          </div>
        </div>
      </div>

      <div class="flex-1 overflow-y-auto px-4 space-y-6 custom-scrollbar">

        <!-- Dynamic Nav -->
        <div>
          <h3 class="text-[9px] text-slate-500 font-bold uppercase tracking-[0.2em] px-3 mb-2">Navegação</h3>
          <nav class="space-y-1">
            <NuxtLink 
              v-for="item in navigationItems" 
              :key="item.label"
              :to="item.to"
              class="flex items-center justify-between px-3 py-2.5 rounded-xl transition-all outline-none uppercase text-[11px]"
              :class="isActive(item.to) ? 'bg-surface-container text-[#c9bfff] font-bold' : 'text-slate-500 hover:text-[#aec6ff] hover:bg-surface-container font-medium'"
              @click="closeSidebar"
            >
              <div class="flex items-center gap-3">
                <span class="material-symbols-outlined text-[20px]" :style="isActive(item.to) ? 'font-variation-settings: \'FILL\' 1;' : ''">{{ item.icon }}</span>
                <span>{{ item.label }}</span>
              </div>
              <span v-if="item.badge" class="px-2 py-0.5 rounded-full bg-primary/20 text-primary text-[9px] font-bold">
                {{ item.badge }}
              </span>
            </NuxtLink>
          </nav>
        </div>

        <!-- Configure Nav -->
        <div>
          <h3 class="text-[9px] text-slate-500 font-bold uppercase tracking-[0.2em] px-3 mb-2">Configuração</h3>
          <nav class="space-y-1">
            <NuxtLink 
              v-for="item in configureItems" 
              :key="item.label"
              :to="item.to"
              class="flex items-center gap-3 px-3 py-2.5 rounded-xl transition-all outline-none uppercase text-[11px]"
              :class="isActive(item.to) ? 'bg-surface-container text-[#c9bfff] font-bold' : 'text-slate-500 hover:text-[#aec6ff] hover:bg-surface-container font-medium'"
              @click="closeSidebar"
            >
              <span class="material-symbols-outlined text-[20px]" :style="isActive(item.to) ? 'font-variation-settings: \'FILL\' 1;' : ''">{{ item.icon }}</span>
              <span>{{ item.label }}</span>
            </NuxtLink>
          </nav>
        </div>
      </div>

      <!-- Promo Card -->
      <div class="px-4 mt-6">
        <div class="bg-linear-to-b from-primary/20 to-surface-container rounded-2xl p-4 border border-outline-variant/10 text-center relative overflow-hidden">
          <div class="absolute inset-0 bg-primary/5 blur-xl"></div>
          <div class="relative z-10 flex flex-col items-center">
            <div class="w-10 h-10 bg-primary text-on-primary rounded-xl flex items-center justify-center mb-3 shadow-[0_0_15px_rgba(69,22,205,0.4)]">
              <span class="material-symbols-outlined text-xl">account_balance_wallet</span>
            </div>
            <h4 class="text-white text-xs font-bold font-headline mb-1 uppercase tracking-wider">Recarregue sua Wallet</h4>
            <p class="text-[9px] text-slate-300 mb-4 leading-relaxed tracking-wider">Adicione fundos para participar de Torneios Pro com exclusividade.</p>
            <NuxtLink to="/wallet" class="w-full py-2 bg-linear-to-br from-primary-container to-[#2c1370] border border-primary/20 hover:border-primary/50 text-white rounded-lg text-[10px] font-bold uppercase tracking-widest transition-all outline-none shadow-lg">
              Adicionar Fundos
            </NuxtLink>
          </div>
        </div>
      </div>

    </div>
  </aside>
</template>

<style scoped>
.font-headline {
  font-family: 'Space Grotesk', sans-serif;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.no-scrollbar::-webkit-scrollbar {
  display: none;
}
.no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.custom-scrollbar::-webkit-scrollbar {
  width: 3px;
}
.custom-scrollbar::-webkit-scrollbar-track {
  background: transparent;
}
.custom-scrollbar::-webkit-scrollbar-thumb {
  background: rgba(255,255,255,0.05);
  border-radius: 4px;
}
</style>

