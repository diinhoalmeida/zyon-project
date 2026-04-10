<script setup lang="ts">
defineProps<{
  availableBalance: string
  pendingBalance: string
  monthlyGrowth: string
}>()
</script>

<template>
  <section class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-12">
    <!-- Main Balance -->
    <div class="md:col-span-2 bg-surface-container-low p-10 rounded-xl relative overflow-hidden flex flex-col justify-between min-h-[280px]">
      <div class="absolute -right-12 -top-12 w-64 h-64 bg-primary/10 rounded-full blur-3xl"></div>
      <div>
        <p class="text-xs uppercase tracking-widest text-slate-400 mb-2 font-label">Available Balance</p>
        <div class="text-7xl font-bold font-headline text-on-surface tracking-tighter">{{ availableBalance }}</div>
      </div>
      <div class="flex gap-4 items-center">
        <div class="flex items-center gap-2 text-primary font-bold text-sm bg-primary/10 px-4 py-2 rounded-full">
          <span class="material-symbols-outlined text-sm">trending_up</span>
          {{ monthlyGrowth }} this month
        </div>
        <div class="text-xs text-slate-500 font-label uppercase">Updated 2 minutes ago</div>
      </div>
    </div>

    <!-- Pending Balance -->
    <div class="bg-surface-container-highest/30 backdrop-blur-md p-8 rounded-xl flex flex-col justify-between border border-outline-variant/10">
      <div>
        <p class="text-xs uppercase tracking-widest text-slate-400 mb-2 font-label">Pending Balance</p>
        <div class="text-4xl font-bold font-headline text-on-tertiary-container">{{ pendingBalance }}</div>
      </div>
      <div class="space-y-4">
        <p class="text-xs text-slate-400 leading-relaxed font-body">Funds currently held in escrow from active tournaments. Released after completion.</p>
        <a class="text-xs font-bold uppercase tracking-widest text-secondary hover:underline flex items-center gap-1" href="#">
          View details
          <span class="material-symbols-outlined text-xs">arrow_forward</span>
        </a>
      </div>
    </div>
  </section>
</template>
