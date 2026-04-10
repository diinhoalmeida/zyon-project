<script setup lang="ts">
// Security Level component with circular progress
</script>

<template>
  <div class="bg-surface-container-low rounded-xl p-5 sm:p-6 lg:p-8 relative overflow-hidden">
    <div class="absolute -right-4 -top-4 w-32 h-32 bg-secondary/5 blur-[40px] rounded-full"></div>
    <h3 class="text-lg lg:text-xl font-headline font-bold text-slate-200 mb-4 lg:mb-6">Security Level</h3>
    <div class="flex flex-col items-center text-center py-2 lg:py-4">
      <div class="relative w-32 h-32 lg:w-40 lg:h-40 mb-4 lg:mb-6">
        <!-- Circular Progress Mock -->
        <svg class="w-full h-full transform -rotate-90" viewBox="0 0 160 160">
          <circle class="text-surface-container-highest" cx="80" cy="80" fill="transparent" r="70" stroke="currentColor" stroke-width="8"></circle>
          <circle class="text-secondary" cx="80" cy="80" fill="transparent" r="70" stroke="currentColor" stroke-dasharray="440" stroke-dashoffset="66" stroke-width="8"></circle>
        </svg>
        <div class="absolute inset-0 flex flex-col items-center justify-center">
          <span class="text-3xl lg:text-4xl font-headline font-bold text-slate-200">A+</span>
          <span class="text-[10px] text-slate-500 uppercase font-bold">Optimized</span>
        </div>
      </div>
      <p class="text-[10px] lg:text-xs text-slate-400 mb-4 lg:mb-6 leading-relaxed max-w-[240px]">System integrity is currently at peak performance. No critical threats detected in the last 72 hours.</p>
      <button class="w-full py-2.5 lg:py-3 rounded-lg border border-outline-variant/20 text-[10px] lg:text-xs font-bold uppercase tracking-widest text-secondary hover:bg-secondary/10 transition-colors active:scale-[0.98]">
        Run Global Scan
      </button>
    </div>
  </div>
</template>
