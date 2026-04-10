<script setup lang="ts">
defineProps<{
  type: 'reward' | 'protocol'
  title?: string
  subtitle?: string
  value?: string
  icon?: string
  details?: { label: string, value: string, color?: string }[]
}>()
</script>

<template>
  <div 
    v-if="type === 'reward'" 
    class="grow p-8 rounded-3xl bg-surface-container border border-outline-variant/10 relative overflow-hidden"
  >
    <div class="absolute top-0 right-0 p-4">
      <span class="material-symbols-outlined text-primary/20 text-6xl">military_tech</span>
    </div>
    <p class="text-xs font-headline uppercase tracking-widest text-slate-500 mb-2">{{ subtitle }}</p>
    <h4 class="text-4xl font-headline font-bold text-[#c9bfff] mb-6">{{ value }}</h4>
    <div class="space-y-4">
      <div 
        v-for="(detail, index) in (details || [])" 
        :key="index"
        class="flex justify-between items-center py-3 border-outline-variant/10"
        :class="{ 'border-b': index !== details.length - 1 }"
      >
        <span class="text-sm text-slate-400">{{ detail.label }}</span>
        <span 
          class="text-sm font-bold"
          :class="detail.color || 'text-white'"
        >{{ detail.value }}</span>
      </div>
    </div>
  </div>

  <div 
    v-else-if="type === 'protocol'" 
    class="p-8 rounded-3xl bg-primary-container text-on-primary-container relative overflow-hidden"
  >
    <div class="relative z-10">
      <h4 class="font-headline font-bold mb-2">{{ title }}</h4>
      <p class="text-xs opacity-70 mb-4 leading-relaxed">{{ subtitle }}</p>
      <button class="w-full py-3 bg-on-primary-container text-primary-container rounded-xl font-headline text-xs font-bold uppercase tracking-widest">
        Read Rules
      </button>
    </div>
    <div class="absolute -right-4 -bottom-4 opacity-10">
      <span class="material-symbols-outlined text-9xl">{{ icon || 'gavel' }}</span>
    </div>
  </div>
</template>
