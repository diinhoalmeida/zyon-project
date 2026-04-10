<script setup lang="ts">
defineProps<{
  name: string
  id: string
  prizePool: string
  status: string
  image: string
  participants: string
  statusClass?: string
  actionIcon?: string
  actionClass?: string
}>()
</script>

<template>
  <div class="rounded-xl bg-surface-container-low overflow-hidden group hover:translate-y-[-4px] transition-all duration-200 border border-outline-variant/10 active:scale-[0.98]">
    <div class="relative h-28 sm:h-32 w-full">
      <img :src="image" class="w-full h-full object-cover" :alt="name" />
      <div class="absolute inset-0 bg-gradient-to-t from-surface-container-low to-transparent"></div>
      <span :class="['absolute top-3 right-3 sm:top-4 sm:right-4 px-2.5 sm:px-3 py-1 rounded-full bg-[#10102e]/80 backdrop-blur-md text-[10px] font-bold uppercase tracking-widest', statusClass || 'text-primary']">{{ status }}</span>
    </div>
    <div class="p-4 sm:p-5 lg:p-6">
      <div class="flex justify-between items-start mb-3 lg:mb-4">
        <div class="min-w-0 mr-3">
          <h4 class="font-headline font-bold text-base lg:text-lg text-slate-200 leading-tight truncate">{{ name }}</h4>
          <p class="text-[10px] lg:text-xs text-slate-500">ID: {{ id }}</p>
        </div>
        <div class="text-right shrink-0">
          <p :class="['text-sm font-bold', statusClass || 'text-[#c9bfff]']">{{ prizePool }}</p>
          <p class="text-[10px] text-slate-500 uppercase">Prize Pool</p>
        </div>
      </div>
      <div class="flex items-center gap-3 lg:gap-4 mb-4 lg:mb-6">
        <div class="flex -space-x-2">
          <div class="w-7 h-7 rounded-full bg-surface-container-highest border-2 border-surface-container-low flex items-center justify-center text-[10px] text-slate-300">
            {{ participants }}
          </div>
        </div>
        <span class="text-[10px] lg:text-xs text-slate-400 font-label">Participating</span>
      </div>
      <div class="flex gap-2">
        <button class="flex-1 py-2 lg:py-2.5 rounded-lg bg-surface-container-high text-xs font-bold text-slate-300 hover:text-white transition-colors active:scale-[0.97]">Actions</button>
        <button v-if="actionIcon" :class="['px-3 py-2 lg:py-2.5 rounded-lg bg-surface-container-high transition-colors active:scale-[0.97]', actionClass || 'text-slate-400']">
          <span class="material-symbols-outlined text-lg">{{ actionIcon }}</span>
        </button>
      </div>
    </div>
  </div>
</template>
