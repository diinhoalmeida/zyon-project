<script setup lang="ts">
defineProps<{
  title: string
  value: string
  trend?: string
  icon: string
  iconColorClass?: string
  borderColorClass?: string
  trendColorClass?: string
}>()
</script>

<template>
  <div :class="['rounded-xl bg-surface-container-low p-4 sm:p-5 lg:p-6 flex flex-col justify-between border-l-4 hover:scale-[1.02] transition-transform duration-200', borderColorClass || 'border-primary']">
    <div class="flex justify-between items-center">
      <span :class="['material-symbols-outlined text-2xl lg:text-3xl', iconColorClass || 'text-primary']">{{ icon }}</span>
      <span v-if="trend" :class="['text-[10px] lg:text-xs font-bold', trendColorClass || 'text-emerald-400']">{{ trend }}</span>
    </div>
    <div class="mt-3 lg:mt-4">
      <h4 class="text-2xl lg:text-3xl font-headline font-bold">{{ value }}</h4>
      <p class="text-[10px] lg:text-xs text-slate-500 uppercase tracking-widest mt-1">{{ title }}</p>
    </div>
  </div>
</template>
