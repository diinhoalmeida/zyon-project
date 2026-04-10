<script setup lang="ts">
defineProps<{
  balance: string
  pendingBalance: string
}>()
</script>

<template>
  <section class="grid grid-cols-12 gap-8 items-end mb-12">
    <div class="col-span-12 lg:col-span-7">
      <span class="text-xs uppercase tracking-[0.3em] text-secondary mb-4 block font-label">Financial Overview</span>
      <h2 class="text-6xl font-black font-headline text-on-surface leading-none mb-2">My Assets</h2>
      <p class="text-slate-500 max-w-md font-body text-sm">Manage your earnings from tournaments and marketplace sales. Your funds are secured by Zyon Kinetic protocols.</p>
    </div>
    <div class="col-span-12 lg:col-span-5 flex justify-end">
      <button class="group relative px-10 py-5 bg-gradient-to-br from-primary to-primary-container text-on-primary font-headline font-bold uppercase tracking-widest rounded-full shadow-[0_20px_40px_-5px_rgba(69,22,205,0.4)] transition-all hover:scale-[1.02] active:scale-95">
        Solicitar Saque
        <span class="ml-2 text-xs opacity-70">(Request Withdrawal)</span>
      </button>
    </div>
  </section>
</template>
