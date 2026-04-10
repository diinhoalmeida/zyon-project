<script setup lang="ts">
defineProps<{
  label: string
  value: string
  icon: string
  color: 'primary' | 'secondary' | 'tertiary'
}>()
</script>

<template>
  <div class="p-8 rounded-3xl bg-surface-container-low border border-outline-variant/5 flex items-center justify-between group hover:bg-surface-container transition-colors">
    <div>
      <p class="text-xs font-headline uppercase tracking-widest text-slate-500 mb-1">{{ label }}</p>
      <h3 
        class="text-4xl font-headline font-bold text-white transition-colors"
        :class="{
          'group-hover:text-primary': color === 'primary',
          'group-hover:text-secondary': color === 'secondary',
          'group-hover:text-tertiary': color === 'tertiary'
        }"
      >
        {{ value }}
      </h3>
    </div>
    <div class="w-16 h-16 rounded-2xl bg-surface-container-high flex items-center justify-center">
      <span 
        class="material-symbols-outlined text-3xl"
        :class="{
          'text-primary': color === 'primary',
          'text-secondary': color === 'secondary',
          'text-tertiary': color === 'tertiary'
        }"
      >
        {{ icon }}
      </span>
    </div>
  </div>
</template>
