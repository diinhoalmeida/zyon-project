<script setup lang="ts">
defineProps<{
  name: string
  series: string
  image: string
  avatars: string[]
  extraParticipants: number
  isLive?: boolean
}>()
</script>

<template>
  <div class="lg:col-span-8 relative overflow-hidden rounded-3xl bg-surface-container-low group min-h-[400px]">
    <div class="absolute inset-0 bg-linear-to-t from-surface-dim via-transparent to-transparent z-10"></div>
    <img 
      class="absolute inset-0 w-full h-full object-cover opacity-60 group-hover:scale-105 transition-transform duration-700" 
      :src="image" 
      :alt="name"
    />
    <div class="absolute bottom-0 left-0 p-10 z-20 w-full">
      <div class="flex items-center gap-3 mb-4">
        <span 
          v-if="isLive" 
          class="px-3 py-1 bg-primary text-on-primary text-[10px] font-bold uppercase tracking-widest rounded-full"
        >
          AO VIVO
        </span>
        <span class="text-secondary text-[10px] font-bold uppercase tracking-widest">{{ series }}</span>
      </div>
      <h3 class="text-3xl sm:text-5xl font-headline font-bold text-white mb-4 leading-tight tracking-tighter" v-html="name"></h3>
      <div class="flex items-center gap-8">
        <div class="flex -space-x-3">
          <img 
            v-for="(avatar, index) in avatars" 
            :key="index"
            class="w-10 h-10 rounded-full border-2 border-surface" 
            :src="avatar" 
            alt="Avatar"
          />
          <div v-if="extraParticipants > 0" class="w-10 h-10 rounded-full border-2 border-surface bg-surface-container-highest flex items-center justify-center text-[10px] font-bold">
            +{{ extraParticipants }}
          </div>
        </div>
        <button class="flex items-center gap-2 text-primary font-headline text-sm uppercase tracking-widest hover:translate-x-2 transition-transform">
          Entrar no Lobby
          <span class="material-symbols-outlined text-sm">arrow_forward</span>
        </button>
      </div>
    </div>
  </div>
</template>
