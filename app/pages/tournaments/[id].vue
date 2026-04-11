<script setup lang="ts">
import { ref } from 'vue'
import { useRoute } from 'vue-router'
import DetailsHero from '~/components/tournaments/DetailsHero.vue'
import PrizePool from '~/components/tournaments/PrizePool.vue'
import GroupRankings from '~/components/tournaments/GroupRankings.vue'
import RulesContent from '~/components/tournaments/RulesContent.vue'
import EntryConfirmationModal from '~/components/tournaments/EntryConfirmationModal.vue'

/**
 * Tournament Details Page
 * Dynamic route to handle individual tournaments.
 */

const route = useRoute()
const tournamentId = route.params.id

// Mock data fetching based on ID
const tournamentData = {
  id: tournamentId,
  title: 'CYBER STRIKE ELITE',
  game: 'Neon Siege',
  image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuA0JPYvbLE4Z2o1t-FiXxrjfnY59bKItPDGJYoRhEZN2FcA-dUV6fRJ1cV82VU8Ve7l4gRcbWIbFbMBVo2BcJRPL4CbFUuB_xpUyw8l1rnbscR2psjx9WDX0m5tm4UBy1Dwwd6oHFygW6ru8yhzeu9OPLzVKONiW3koHe1xabA5Z2Ce5OgwVjwlGRocji6AAqKs3GOL-VBMg--OJeNuzzVqEHSuVhECPmqedFxVO--j_PCHWCT_I6a593GM1h420nZ2vGCuPvA1PqY',
  prizePool: '$12,500',
  status: 'Inscrições Abertas',
  statusClass: 'bg-green-500/10 text-green-400 border-green-500/20',
  organizerName: 'Zyon Official',
  organizerLogo: 'https://i.pravatar.cc/150?u=zyon', // Placeholder logo
  participants: 128,
  maxParticipants: 256,
  feeReal: '$ 15.00',
  feeZyon: '1.500',
  penaltyPercentage: 30
}

useHead({
  title: `${tournamentData.title} | Zyon Tournaments`,
  bodyAttrs: {
    class: 'bg-background text-on-surface selection:bg-primary selection:text-on-primary'
  }
})

// Tab Management
type Tab = 'overview' | 'ranking' | 'rules'
const activeTab = ref<Tab>('overview')

const tabs = [
  { id: 'overview', label: 'Visão Geral', icon: 'dashboard' },
  { id: 'ranking', label: 'Fase de Grupos', icon: 'leaderboard' },
  { id: 'rules', label: 'Regras', icon: 'gavel' }
]

// Modal State
const isModalOpen = ref(false)

const handleEntryConfirm = (method: 'fiat' | 'zyon') => {
  console.log('User confirmed entry using:', method)
  isModalOpen.value = false
  // Lógica futura de dedução de saldo aqui
}
</script>

<template>
  <div class="dark min-h-screen bg-background text-on-surface">
    <AdminSidebar />

    <main class="min-h-screen transition-[padding] duration-300 lg:pl-[280px]">
      <AdminHeader />

      <div class="pt-20 lg:pt-24 px-4 sm:px-10 lg:px-12 pb-12 max-w-screen-2xl mx-auto">
        <!-- Back Button -->
        <NuxtLink to="/tournaments" class="inline-flex items-center gap-2 text-slate-400 hover:text-white transition-colors mb-6 group">
          <span class="material-symbols-outlined text-sm group-hover:-translate-x-1 transition-transform">arrow_back</span>
          <span class="text-xs font-bold uppercase tracking-widest">Voltar para Arena</span>
        </NuxtLink>

        <DetailsHero 
          v-bind="tournamentData" 
          @join-click="isModalOpen = true"
        />

        <!-- Navigation Tabs -->
        <div class="flex items-center gap-2 mb-8 border-b border-outline-variant/10 pb-4 overflow-x-auto custom-scrollbar">
          <button
            v-for="tab in tabs"
            :key="tab.id"
            @click="activeTab = tab.id as Tab"
            class="flex items-center gap-2 px-6 py-3 rounded-full font-bold text-xs uppercase tracking-[0.2em] transition-all whitespace-nowrap outline-none"
            :class="activeTab === tab.id 
              ? 'bg-primary text-on-primary shadow-lg shadow-primary/20' 
              : 'bg-surface-container-low text-slate-400 hover:text-white hover:bg-surface-container border border-outline-variant/10'"
          >
            <span class="material-symbols-outlined text-sm">{{ tab.icon }}</span>
            {{ tab.label }}
          </button>
        </div>

        <!-- Tab Content -->
        <div class="min-h-[400px]">
          <!-- Overview Tab -->
          <Transition name="fade" mode="out-in">
            <div v-if="activeTab === 'overview'" class="space-y-6">
              <PrizePool :totalPrize="tournamentData.prizePool" />
            </div>
            
            <!-- Ranking Tab -->
            <div v-else-if="activeTab === 'ranking'">
              <GroupRankings />
            </div>

            <!-- Rules Tab -->
            <div v-else-if="activeTab === 'rules'">
              <RulesContent />
            </div>
          </Transition>
        </div>

        <AdminFooter class="mt-12" />
        
        <!-- Payment Modal -->
        <EntryConfirmationModal 
          :is-open="isModalOpen"
          :tournament-title="tournamentData.title"
          :fee-real="tournamentData.feeReal"
          :fee-zyon="tournamentData.feeZyon"
          :penalty-percentage="tournamentData.penaltyPercentage"
          @close="isModalOpen = false"
          @confirm="handleEntryConfirm"
        />
      </div>
    </main>
  </div>
</template>

<style scoped>
.custom-scrollbar::-webkit-scrollbar {
  height: 4px;
}
.custom-scrollbar::-webkit-scrollbar-track {
  background: transparent;
}
.custom-scrollbar::-webkit-scrollbar-thumb {
  background: rgba(255,255,255,0.1);
  border-radius: 4px;
}

/* Transitions */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
</style>
