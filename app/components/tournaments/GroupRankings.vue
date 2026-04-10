<script setup lang="ts">
import { ref, computed } from 'vue'

/**
 * GroupRankings Component
 * Shows leaderboard separated by randomly assigned groups.
 */

interface Player {
  id: string
  name: string
  avatar: string
  points: number
  matchesPlayed: number
  winRate: number
  trend: 'up' | 'down' | 'same'
}

interface Group {
  id: string
  name: string
  players: Player[]
  isUserGroup?: boolean
}

// Mock Data
const groups = ref<Group[]>([
  {
    id: 'g1',
    name: 'Grupo 1',
    isUserGroup: true,
    players: [
      { id: 'p1', name: 'Althea_N', avatar: 'https://i.pravatar.cc/150?u=p1', points: 1450, matchesPlayed: 5, winRate: 80, trend: 'up' },
      { id: 'p2', name: 'CyberKing', avatar: 'https://i.pravatar.cc/150?u=p2', points: 1320, matchesPlayed: 5, winRate: 60, trend: 'up' },
      { id: 'p3', name: 'Zyon_Pro', avatar: 'https://i.pravatar.cc/150?u=p3', points: 1200, matchesPlayed: 4, winRate: 75, trend: 'down' },
      { id: 'p4', name: 'NeonNinja', avatar: 'https://i.pravatar.cc/150?u=p4', points: 950, matchesPlayed: 5, winRate: 40, trend: 'same' },
      { id: 'p5', name: 'VoidRunner09', avatar: 'https://i.pravatar.cc/150?u=p5', points: 800, matchesPlayed: 3, winRate: 33, trend: 'down' }
    ]
  },
  {
    id: 'g2',
    name: 'Grupo 2',
    players: [
      { id: 'p6', name: 'Luna_Star', avatar: 'https://i.pravatar.cc/150?u=p6', points: 1500, matchesPlayed: 5, winRate: 100, trend: 'same' },
      { id: 'p7', name: 'DriftMax', avatar: 'https://i.pravatar.cc/150?u=p7', points: 1250, matchesPlayed: 4, winRate: 75, trend: 'up' },
      { id: 'p8', name: 'RogueOne', avatar: 'https://i.pravatar.cc/150?u=p8', points: 1100, matchesPlayed: 5, winRate: 60, trend: 'down' },
      { id: 'p9', name: 'Glitch_0x', avatar: 'https://i.pravatar.cc/150?u=p9', points: 900, matchesPlayed: 5, winRate: 40, trend: 'up' }
    ]
  }
])

const activeGroupId = ref('g1')

const activeGroup = computed(() => {
  return groups.value.find(g => g.id === activeGroupId.value) || groups.value[0]
})

// Sort players by points descending
const sortedPlayers = computed(() => {
  if (!activeGroup.value) return []
  return [...activeGroup.value.players].sort((a, b) => b.points - a.points)
})
</script>

<template>
  <div class="bg-surface-container-low border border-outline-variant/10 rounded-2xl overflow-hidden shadow-2xl backdrop-blur-sm">
    <!-- Header & Group Selector -->
    <div class="p-6 sm:p-8 border-b border-outline-variant/10">
      <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-6">
        <div>
          <h3 class="text-2xl font-headline font-bold text-white tracking-wide">Ranking da Fase de Grupos</h3>
          <div class="flex items-center gap-2 mt-1">
            <span class="material-symbols-outlined text-[12px] text-primary">info</span>
            <p class="text-xs text-slate-400 uppercase tracking-widest leading-relaxed">Você é alocado automaticamente.<br/> Quando um grupo lota (ex: 30 pessoas), um novo é criado.</p>
          </div>
        </div>
        
        <!-- Group Tabs -->
        <div class="flex gap-2 p-1 bg-surface-container-highest rounded-xl overflow-x-auto custom-scrollbar border border-outline-variant/10 max-w-full sm:max-w-md">
          <button 
            v-for="group in groups" 
            :key="group.id"
            @click="activeGroupId = group.id"
            class="relative px-5 py-2.5 rounded-lg text-xs font-bold uppercase tracking-widest whitespace-nowrap transition-all outline-none flex items-center gap-2"
            :class="activeGroupId === group.id ? 'bg-primary text-on-primary shadow-md' : 'text-slate-400 hover:text-white hover:bg-surface-container'"
          >
            {{ group.name }}
            <span v-if="group.isUserGroup && activeGroupId !== group.id" class="w-2 h-2 rounded-full bg-primary absolute top-2 right-2 shadow-[0_0_8px_rgba(201,191,255,0.8)]"></span>
            <span v-if="group.isUserGroup && activeGroupId === group.id" class="text-[9px] bg-primary-container text-on-primary px-1.5 py-0.5 rounded ml-1">SEU</span>
          </button>
        </div>
      </div>
    </div>

    <!-- Leaderboard Table -->
    <div class="overflow-x-auto">
      <table class="w-full text-left border-collapse min-w-[600px]">
        <thead>
          <tr class="bg-surface-container-high/30 border-b border-outline-variant/10">
            <th class="px-6 py-4 text-[10px] uppercase tracking-[0.3em] text-slate-500 font-bold w-16 text-center">Pos</th>
            <th class="px-6 py-4 text-[10px] uppercase tracking-[0.3em] text-slate-500 font-bold">Jogador</th>
            <th class="px-6 py-4 text-[10px] uppercase tracking-[0.3em] text-slate-500 font-bold text-center">Partidas</th>
            <th class="px-6 py-4 text-[10px] uppercase tracking-[0.3em] text-slate-500 font-bold text-center">Vitórias</th>
            <th class="px-6 py-4 text-[10px] uppercase tracking-[0.3em] text-slate-500 font-bold text-right w-32">Pontuação</th>
          </tr>
        </thead>
        <tbody class="divide-y divide-outline-variant/5">
          <tr 
            v-for="(player, index) in sortedPlayers" 
            :key="player.id"
            class="hover:bg-primary/5 transition-colors group"
          >
            <!-- Position -->
            <td class="px-6 py-4">
              <div class="flex flex-col items-center gap-1">
                <span 
                  class="font-bold text-base"
                  :class="{
                    'text-yellow-500 text-lg': index === 0,
                    'text-slate-300': index === 1,
                    'text-amber-600': index === 2,
                    'text-slate-500': index > 2
                  }"
                >
                  {{ index + 1 }}º
                </span>
                <span v-if="player.trend === 'up'" class="material-symbols-outlined text-[10px] text-green-400">arrow_upward</span>
                <span v-else-if="player.trend === 'down'" class="material-symbols-outlined text-[10px] text-red-400">arrow_downward</span>
                <span v-else class="material-symbols-outlined text-[10px] text-slate-600">horizontal_rule</span>
              </div>
            </td>

            <!-- Player -->
            <td class="px-6 py-4">
              <div class="flex items-center gap-3 relative">
                <!-- Highlight current user row (mock logic: ID ends with 1 is active user) -->
                <div v-if="player.id === 'p1'" class="absolute -left-3 w-1 h-8 bg-primary rounded-r-full"></div>
                
                <img :src="player.avatar" :alt="player.name" class="w-10 h-10 rounded-full border border-outline-variant/20 object-cover" />
                <div class="flex flex-col">
                  <span class="font-bold text-white tracking-wide flex items-center gap-2">
                    {{ player.name }}
                    <span v-if="player.id === 'p1'" class="px-2 py-0.5 bg-primary/20 text-primary text-[8px] uppercase tracking-widest rounded border border-primary/20">Você</span>
                  </span>
                </div>
              </div>
            </td>

            <!-- Matches -->
            <td class="px-6 py-4 text-center">
              <span class="text-white font-bold tabular-nums">{{ player.matchesPlayed }}</span>
            </td>

            <!-- Win Rate -->
            <td class="px-6 py-4">
              <div class="flex items-center justify-center gap-2">
                <span class="text-sm font-bold text-white tabular-nums">{{ player.winRate }}%</span>
                <!-- Mini Progress -->
                <div class="w-12 h-1 bg-surface-container-highest rounded-full overflow-hidden hidden sm:block">
                  <div class="h-full bg-primary/60" :style="{ width: player.winRate + '%' }"></div>
                </div>
              </div>
            </td>

            <!-- Points -->
            <td class="px-6 py-4 text-right">
              <span class="text-xl font-headline font-bold text-primary tabular-nums tracking-tight">{{ player.points }}</span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
.font-headline {
  font-family: 'Space Grotesk', sans-serif;
}
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
</style>
