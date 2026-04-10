<script setup lang="ts">
// Large Growth Card component with mock chart
</script>

<template>
  <div class="sm:col-span-2 sm:row-span-2 rounded-xl bg-surface-container-low p-5 sm:p-6 lg:p-8 relative overflow-hidden flex flex-col justify-between group">
    <div class="absolute -right-12 -top-12 w-48 lg:w-64 h-48 lg:h-64 bg-primary/10 blur-[100px] rounded-full group-hover:bg-primary/20 transition-colors"></div>
    <div>
      <div class="flex justify-between items-start mb-6 lg:mb-8">
        <div class="space-y-1">
          <span class="text-[10px] lg:text-xs uppercase tracking-widest text-slate-500 font-medium">Platform Growth</span>
          <h3 class="text-3xl lg:text-4xl font-headline font-bold">+124.8%</h3>
        </div>
        <span class="px-2 lg:px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-[10px] lg:text-xs font-bold shrink-0">LIFETIME</span>
      </div>
      <!-- Mock Chart -->
      <div class="h-32 sm:h-40 lg:h-48 flex items-end gap-1.5 lg:gap-2 mb-4">
        <div class="flex-1 bg-surface-container-highest rounded-t-lg h-[30%] hover:bg-primary/40 transition-colors"></div>
        <div class="flex-1 bg-surface-container-highest rounded-t-lg h-[45%] hover:bg-primary/40 transition-colors"></div>
        <div class="flex-1 bg-surface-container-highest rounded-t-lg h-[40%] hover:bg-primary/40 transition-colors"></div>
        <div class="flex-1 bg-surface-container-highest rounded-t-lg h-[65%] hover:bg-primary/40 transition-colors"></div>
        <div class="flex-1 bg-surface-container-highest rounded-t-lg h-[55%] hover:bg-primary/40 transition-colors"></div>
        <div class="flex-1 bg-primary/60 rounded-t-lg h-[85%]"></div>
        <div class="flex-1 bg-primary rounded-t-lg h-[100%]"></div>
      </div>
    </div>
    <div class="flex justify-between items-center text-[10px] lg:text-xs text-slate-500 font-label tracking-wide uppercase">
      <span>Jan 2024</span>
      <span>May 2024</span>
      <span>Today</span>
    </div>
  </div>
</template>
