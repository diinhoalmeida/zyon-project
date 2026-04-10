<script setup lang="ts">
import DashboardHero from '~/components/dashboard/DashboardHero.vue'
import DashboardStatCard from '~/components/dashboard/DashboardStatCard.vue'
import MatchHistoryTable from '~/components/dashboard/MatchHistoryTable.vue'
import TournamentTable from '~/components/tournaments/TournamentTable.vue'

useHead({
  title: 'Zyon | Dashboard de Jogos',
  bodyAttrs: {
    class: 'bg-background text-on-background selection:bg-primary selection:text-on-primary'
  }
})

const activeTournament = {
  name: 'Cyber-Protocol: <br/>Origins 2024',
  series: 'Série do Campeonato Global',
  image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuDSRmPzMIGm7T-Un916XVoiVadS64q1XxBFpe6JzmIhg5TQjTD7O59dZTnEa5oAnnHLXQS-LpihcGUijSd4EL1VUuwkVJbAmYaOBHqOtvdIh1cc0Oqvg_NnY_7lphogaUUC5H1Q3_zPQswnWhFEU1v_n1tYNWdgNNANvqyvV0y4tgZdSnDIKIi8-w6ifoA_DXp6KTOW27l-UZOwgHYVf_tmb36GzWQE0oJ09GtcHPdZNG_Ei7EdwWCMMBSuUIjP9Ki7DFL2AFB-7r4',
  avatars: [
    'https://lh3.googleusercontent.com/aida-public/AB6AXuDCGs-OhgSsGkIELVYs-m_o6kbqW_gFcAegsvwnb9pE2RAtZSAsMKZEjYDICE-SQ88MfKDYmBTvCNS_0a5XHtZX-XdgylEGrPSyyW84-4vKrrQYoF55KYkknYdmnzMUCctVblhGAz4zjBOD5tBtZF8wimzCGYeQePAsE-45ZtshEJtRKc8a-N7uJDb9diWG8XNo-pZCD_J3fUpQ-c2weJE0Xp_GSYvYekxgKKXNsUTM-AS3cLZmYdCM2wmEKOXu660P3zlnXAslu8I',
    'https://lh3.googleusercontent.com/aida-public/AB6AXuDp0Lap_dA3X2EgCzkNm6OKPA-0mZ_APrMXLavt1qRIdVghNtNrdu4dwYBTT-qpeMQ8fryVr0JtCaO6W3wz5a9CwmOx0hSokeONwA4AMxWi3_5PgcHPhHrIG2dFOQzydowhgOyoAPvSBB7k35H7HKOrA7GNog-KO7IWReXlqUEKlR9FH2h5IjWdm66IECp69w-DazQzy_tCoHzchCxFzKGM0l4MZKI0qWs4sn3oIgmz7pnpT44wz6KnyoI3owJCBYzOLyh43Aob5lc',
    'https://lh3.googleusercontent.com/aida-public/AB6AXuDDL0RDxJ3FdhTlMbMKE9SYJA1w-Xdqw-r6v993rRfEHOHDjfTC37qKWAyzCgZzUS8DosWTHMLz9BQaGk05iSh4Nh6YASH9dR-pJ4iY08MbTlmaDJlmt8X96qIoImaQ7YUGu6pbVR-OfKASmelp2-xjJ86yAhL4bx-5uF6MDiD-wZr88vDdVwtzm9Z4ti8uQn_fpT87K4km8_fI69fAOAQ7rIzKZrefmWLY8aioGAgUDNTia6867I34ZzO9MQCK5tlGq8onLWCxM8I'
  ],
  extraParticipants: 24,
  isLive: true
}

const rewardData = {
  value: '12.5 ZYN',
  subtitle: 'Recompensa Estimada',
  details: [
    { label: 'Posição', value: '#04 / 128' },
    { label: 'Próxima Partida', value: '14:00 GMT' },
    { label: 'Status', value: 'Qualificado', color: 'text-green-400' }
  ]
}

const protocolData = {
  title: 'Protocolo de Torneio',
  subtitle: 'Certifique-se de que seu link neural está estável. Partidas com alta latência estão sujeitas a desclassificação.'
}

const gameStats = [
  { label: 'Ratio KDA', value: '2.4', icon: 'swords', color: 'primary' },
  { label: 'Taxa de Vitória', value: '68%', icon: 'trending_up', color: 'secondary' },
  { label: 'Pontuação Total', value: '12,450', icon: 'workspace_premium', color: 'tertiary' }
] as const

const recentMatches = [
  { 
    mode: 'Arena Ranqueada', 
    map: 'Cyber-Grid', 
    icon: 'videogame_asset', 
    result: 'Vitória', 
    score: '+850 PTS', 
    time: '2 horas atrás',
    victory: true 
  },
  { 
    mode: 'Team Deathmatch', 
    map: 'Neon-District', 
    icon: 'groups', 
    result: 'Derrota', 
    score: '+120 PTS', 
    time: '5 horas atrás',
    victory: false 
  },
  { 
    mode: 'Torneio Blitz', 
    map: 'Eliminatórias Round 1', 
    icon: 'bolt', 
    result: 'Vitória', 
    score: '+1,420 PTS', 
    time: 'Ontem',
    victory: true 
  }
]
</script>

<template>
  <div class="dark min-h-screen bg-[#10102e] text-[#e2dfff] font-['Inter']">
    <AdminSidebar />

    <!-- Main Content Area -->
    <main class="min-h-screen transition-[padding] duration-300 lg:pl-[280px]">
      <AdminHeader />

      <!-- Dashboard Canvas -->
      <div class="pt-20 lg:pt-24 px-4 sm:px-6 lg:px-8 pb-8 lg:pb-12 max-w-screen-2xl mx-auto">
        
        <DashboardHero 
          :tournament="activeTournament"
          :reward="rewardData"
          :protocol="protocolData"
        />

        <!-- Stats Panel -->
        <section class="mb-12">
          <h2 class="text-sm font-headline uppercase tracking-[0.3em] text-primary mb-6">Estatísticas</h2>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <DashboardStatCard 
              v-for="stat in gameStats" 
              :key="stat.label"
              v-bind="stat"
            />
          </div>
        </section>

        <!-- Open Tournaments Section -->
        <section class="mb-12">
          <div class="flex flex-col sm:flex-row sm:items-center justify-between mb-6 gap-4">
            <div>
              <h2 class="text-sm font-headline uppercase tracking-[0.3em] text-primary">Torneios Abertos</h2>
              <p class="text-xs text-slate-400 mt-1">Ingresse em novos torneios e concorra a prêmios em ZYN</p>
            </div>
            <NuxtLink to="/tournaments" class="text-xs font-bold text-slate-300 hover:text-white px-4 py-2 rounded-lg bg-surface-container hover:bg-surface-container-high transition-colors flex items-center gap-2 border border-outline-variant/10">
              Ver Todos <span class="material-symbols-outlined text-sm">arrow_forward</span>
            </NuxtLink>
          </div>
          
          <TournamentTable />
        </section>

        <!-- Match History -->
        <section>
          <div class="mb-6">
            <h2 class="text-sm font-headline uppercase tracking-[0.3em] text-primary">Histórico de Partidas</h2>
          </div>
          <MatchHistoryTable :matches="recentMatches" />
        </section>
      </div>

      <AdminFooter />
    </main>
  </div>
</template>

<style scoped>
.glass-panel {
  background: rgba(50, 49, 81, 0.6);
  backdrop-filter: blur(20px);
}
</style>
