<script setup lang="ts">
/**
 * PrizePool Component
 * Displays the prize distribution for the top 10 ranks.
 */

interface PrizeTier {
  rank: number
  amountPro: string
  amountBasic: string
  percentage: number
}

// Mock distribution data ensuring top 10 win more than typical entry (if any)
const prizeDistribution: PrizeTier[] = [
  { rank: 1, amountPro: '$ 5,000', amountBasic: '$ 3,500', percentage: 40 },
  { rank: 2, amountPro: '$ 2,500', amountBasic: '$ 1,750', percentage: 20 },
  { rank: 3, amountPro: '$ 1,250', amountBasic: '$ 875', percentage: 10 },
  { rank: 4, amountPro: '$ 750', amountBasic: '$ 525', percentage: 6 },
  { rank: 5, amountPro: '$ 500', amountBasic: '$ 350', percentage: 4 },
  { rank: 6, amountPro: '$ 400', amountBasic: '$ 280', percentage: 3.2 },
  { rank: 7, amountPro: '$ 300', amountBasic: '$ 210', percentage: 2.4 },
  { rank: 8, amountPro: '$ 200', amountBasic: '$ 140', percentage: 1.6 },
  { rank: 9, amountPro: '$ 150', amountBasic: '$ 105', percentage: 1.2 },
  { rank: 10, amountPro: '$ 100', amountBasic: '$ 70', percentage: 0.8 }
]

defineProps<{
  totalPrize: string
}>()
</script>

<template>
  <div class="bg-surface-container-low border border-outline-variant/10 rounded-2xl overflow-hidden shadow-2xl backdrop-blur-sm p-6 sm:p-8">
    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 mb-8">
      <div>
        <h3 class="text-2xl font-headline font-bold text-white tracking-wide">Distribuição de Prêmios</h3>
        <p class="text-xs text-slate-400 mt-1 uppercase tracking-widest">Os 10 melhores jogadores dividem o prêmio total</p>
      </div>
      <div class="bg-surface-container-highest px-4 py-3 rounded-xl border border-outline-variant/20 inline-flex items-center gap-3">
        <div class="flex flex-col">
          <span class="text-[9px] uppercase tracking-widest text-slate-500 font-bold mb-0.5">Prêmio Total</span>
          <span class="text-lg font-bold text-primary leading-none">{{ totalPrize }}</span>
        </div>
        <span class="material-symbols-outlined text-primary text-3xl opacity-50" style="font-variation-settings: 'FILL' 1;">emoji_events</span>
      </div>
    </div>

    <div class="overflow-x-auto -mx-6 sm:mx-0 px-6 sm:px-0">
      <table class="w-full text-left border-collapse min-w-[400px]">
        <thead>
          <tr class="border-b border-outline-variant/10">
            <th class="py-4 text-[10px] uppercase tracking-[0.3em] text-slate-500 font-bold w-20">Rank</th>
            <th class="py-4 text-[10px] uppercase tracking-[0.3em] text-slate-500 font-bold">
              <div class="flex flex-col">
                <span class="text-green-400">Prêmio (Pro)</span>
                <span class="text-[8px] text-slate-500 tracking-widest mt-0.5">Inscrição via Dinheiro</span>
              </div>
            </th>
            <th class="py-4 text-[10px] uppercase tracking-[0.3em] text-slate-500 font-bold">
              <div class="flex flex-col">
                <span class="text-primary">Prêmio (Básico)</span>
                <span class="text-[8px] text-slate-500 tracking-widest mt-0.5">Inscrição via Z-Coins</span>
              </div>
            </th>
            <th class="py-4 text-[10px] uppercase tracking-[0.3em] text-slate-500 font-bold text-right">% do Total</th>
          </tr>
        </thead>
        <tbody class="divide-y divide-outline-variant/5">
          <tr 
            v-for="tier in prizeDistribution" 
            :key="tier.rank"
            class="hover:bg-primary/5 transition-colors group"
          >
            <td class="py-4">
              <div class="flex items-center gap-2">
                <span 
                  class="w-8 h-8 rounded-full flex items-center justify-center font-bold text-xs"
                  :class="{
                    'bg-yellow-500/20 text-yellow-500 border border-yellow-500/30 shadow-[0_0_10px_rgba(234,179,8,0.2)]': tier.rank === 1,
                    'bg-slate-300/20 text-slate-300 border border-slate-300/30': tier.rank === 2,
                    'bg-amber-700/20 text-amber-600 border border-amber-700/30': tier.rank === 3,
                    'bg-surface-container-highest text-slate-400 border border-outline-variant/10': tier.rank > 3
                  }"
                >
                  #{{ tier.rank }}
                </span>
                <span v-if="tier.rank === 1" class="material-symbols-outlined text-yellow-500 text-sm hidden sm:block" style="font-variation-settings: 'FILL' 1;">star</span>
              </div>
            </td>
            <td class="py-4">
              <span 
                class="font-bold text-base"
                :class="{
                  'text-green-400 text-lg': tier.rank === 1,
                  'text-white': tier.rank > 1
                }"
              >
                {{ tier.amountPro }}
              </span>
            </td>
            <td class="py-4">
              <span 
                class="font-bold text-base flex items-center gap-2"
                :class="{
                  'text-primary text-lg': tier.rank === 1,
                  'text-slate-300': tier.rank > 1
                }"
              >
                {{ tier.amountBasic }}
                <span v-if="tier.rank === 1" class="text-[9px] bg-red-500/10 text-red-400 border border-red-500/20 px-1.5 py-0.5 rounded uppercase tracking-wider font-bold">-30%</span>
              </span>
            </td>
            <td class="py-4 text-right">
              <div class="flex items-center justify-end gap-3">
                <span class="text-xs font-bold text-slate-400 tabular-nums w-12 text-right">{{ tier.percentage }}%</span>
                <div class="w-24 h-1.5 bg-surface-container-highest rounded-full overflow-hidden hidden sm:block">
                  <div 
                    class="h-full bg-primary/40 rounded-full"
                    :class="{'bg-yellow-500': tier.rank === 1}"
                    :style="{ width: `${tier.percentage * 2}%` }" 
                  ></div>
                </div>
              </div>
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
</style>
