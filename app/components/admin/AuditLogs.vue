<script setup lang="ts">
// Audit Logs section component
</script>

<template>
  <div class="lg:col-span-2 bg-surface-container-low rounded-xl p-5 sm:p-6 lg:p-8">
    <h3 class="text-lg lg:text-xl font-headline font-bold text-slate-200 mb-4 lg:mb-6">System Audit Logs</h3>
    <div class="space-y-3 lg:space-y-4">
      <div class="flex items-center gap-3 lg:gap-4 py-2.5 lg:py-3 border-b border-outline-variant/10 last:border-0">
        <div class="w-9 h-9 lg:w-10 lg:h-10 rounded bg-primary/10 flex items-center justify-center text-primary shrink-0">
          <span class="material-symbols-outlined text-lg lg:text-xl">shield</span>
        </div>
        <div class="flex-1 min-w-0">
          <p class="text-xs sm:text-sm font-medium text-slate-300 truncate">New Admin Role Assigned: <span class="text-primary">alex_zyon</span></p>
          <p class="text-[10px] text-slate-500 uppercase tracking-wider">Today, 2:45 PM</p>
        </div>
        <button class="text-slate-500 hover:text-slate-300 shrink-0">
          <span class="material-symbols-outlined text-xl">chevron_right</span>
        </button>
      </div>
      <div class="flex items-center gap-3 lg:gap-4 py-2.5 lg:py-3 border-b border-outline-variant/10 last:border-0">
        <div class="w-9 h-9 lg:w-10 lg:h-10 rounded bg-secondary/10 flex items-center justify-center text-secondary shrink-0">
          <span class="material-symbols-outlined text-lg lg:text-xl">payments</span>
        </div>
        <div class="flex-1 min-w-0">
          <p class="text-xs sm:text-sm font-medium text-slate-300 truncate">Bulk payout processed for <span class="text-secondary">Zenith Cup</span></p>
          <p class="text-[10px] text-slate-500 uppercase tracking-wider">Today, 11:20 AM</p>
        </div>
        <button class="text-slate-500 hover:text-slate-300 shrink-0">
          <span class="material-symbols-outlined text-xl">chevron_right</span>
        </button>
      </div>
      <div class="flex items-center gap-3 lg:gap-4 py-2.5 lg:py-3 border-b border-outline-variant/10 last:border-0">
        <div class="w-9 h-9 lg:w-10 lg:h-10 rounded bg-error/10 flex items-center justify-center text-error shrink-0">
          <span class="material-symbols-outlined text-lg lg:text-xl" style="font-variation-settings: 'FILL' 1;">warning</span>
        </div>
        <div class="flex-1 min-w-0">
          <p class="text-xs sm:text-sm font-medium text-slate-300 truncate">Suspicious login attempt blocked in <span class="text-error">Node_04</span></p>
          <p class="text-[10px] text-slate-500 uppercase tracking-wider">Yesterday, 11:59 PM</p>
        </div>
        <button class="text-slate-500 hover:text-slate-300 shrink-0">
          <span class="material-symbols-outlined text-xl">chevron_right</span>
        </button>
      </div>
    </div>
  </div>
</template>
