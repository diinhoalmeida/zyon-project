<script setup lang="ts">
interface Match {
  mode: string
  map: string
  icon: string
  result: string
  score: string
  time: string
  victory: boolean
}

defineProps<{
  matches: Match[]
}>()
</script>

<template>
  <section class="mb-12">
    <div class="flex justify-between items-center mb-6">
      <h2 class="text-sm font-headline uppercase tracking-[0.3em] text-primary">Últimas Partidas</h2>
      <button class="text-xs font-headline uppercase tracking-widest text-slate-500 hover:text-white transition-colors">
        Ver Histórico Completo
      </button>
    </div>
    <div class="bg-surface-container-low rounded-3xl overflow-hidden border border-outline-variant/5">
      <div class="overflow-x-auto">
        <table class="w-full text-left">
          <thead>
            <tr class="border-b border-outline-variant/10">
              <th class="px-8 py-5 text-[10px] font-headline uppercase tracking-widest text-slate-500">Modo de Jogo</th>
              <th class="px-8 py-5 text-[10px] font-headline uppercase tracking-widest text-slate-500">Resultado</th>
              <th class="px-8 py-5 text-[10px] font-headline uppercase tracking-widest text-slate-500">Pontuação</th>
              <th class="px-8 py-5 text-[10px] font-headline uppercase tracking-widest text-slate-500">Data/Hora</th>
              <th class="px-8 py-5"></th>
            </tr>
          </thead>
          <tbody class="divide-y divide-outline-variant/5">
            <tr 
              v-for="(match, index) in matches" 
              :key="index"
              class="hover:bg-surface-container-high/50 transition-colors"
            >
              <td class="px-8 py-6">
                <div class="flex items-center gap-4">
                  <div class="w-10 h-10 rounded-lg bg-surface-container flex items-center justify-center">
                    <span class="material-symbols-outlined text-slate-400 text-lg">{{ match.icon }}</span>
                  </div>
                  <div>
                    <p class="text-sm font-bold text-white">{{ match.mode }}</p>
                    <p class="text-[10px] text-slate-500">Mapa: {{ match.map }}</p>
                  </div>
                </div>
              </td>
              <td class="px-8 py-6">
                <span 
                  class="px-3 py-1 text-[10px] font-bold uppercase tracking-widest rounded-full border"
                  :class="match.victory 
                    ? 'bg-green-500/10 text-green-400 border-green-500/20' 
                    : 'bg-red-500/10 text-red-400 border-red-500/20'"
                >
                  {{ match.result }}
                </span>
              </td>
              <td class="px-8 py-6">
                <p 
                  class="text-sm font-headline font-bold"
                  :class="match.victory ? 'text-[#c9bfff]' : 'text-slate-500'"
                >
                  {{ match.score }}
                </p>
              </td>
              <td class="px-8 py-6">
                <p class="text-xs text-slate-400">{{ match.time }}</p>
              </td>
              <td class="px-8 py-6 text-right">
                <button class="p-2 hover:bg-surface-container-highest rounded-full transition-colors">
                  <span class="material-symbols-outlined text-slate-500">more_vert</span>
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </section>
</template>
