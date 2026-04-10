<script setup lang="ts">
useHead({
  title: 'Zyon Admin Central',
  bodyAttrs: {
    class: 'bg-background text-on-background selection:bg-primary selection:text-on-primary'
  }
})
</script>

<template>
  <div class="dark min-h-screen bg-[#10102e] text-[#e2dfff] font-['Inter']">
    <AdminSidebar />

    <!-- Main Content Area -->
    <main class="min-h-screen transition-[padding] duration-300 lg:pl-[280px]">
      <AdminHeader />

      <!-- Dashboard Canvas -->
      <div class="pt-20 lg:pt-24 px-4 sm:px-6 lg:px-8 pb-8 lg:pb-12 max-w-screen-2xl mx-auto">
        <!-- Page Header -->
        <div class="flex flex-col sm:flex-row sm:justify-between sm:items-end gap-4 sm:gap-6 mb-8 lg:mb-12">
          <div class="min-w-0">
            <h2 class="text-3xl sm:text-4xl lg:text-5xl font-['Space_Grotesk'] font-bold tracking-tighter text-on-surface mb-1 lg:mb-2">Admin Central</h2>
            <p class="text-slate-400 max-w-md font-['Inter'] text-sm lg:text-base">Real-time platform oversight and executive control center for the Zyon ecosystem.</p>
          </div>
          <div class="flex gap-3 sm:gap-4 shrink-0">
            <button class="flex-1 sm:flex-none px-4 sm:px-6 py-2.5 sm:py-3 rounded-xl bg-surface-container-high text-on-surface hover:bg-surface-container-highest transition-colors flex items-center justify-center gap-2 text-sm">
              <span class="material-symbols-outlined text-lg">download</span>
              <span class="hidden xs:inline">Export</span>
              <span class="hidden sm:inline"> Report</span>
            </button>
            <button class="flex-1 sm:flex-none px-4 sm:px-6 py-2.5 sm:py-3 rounded-xl bg-primary text-on-primary font-bold hover:opacity-90 transition-opacity flex items-center justify-center gap-2 text-sm">
              <span class="material-symbols-outlined text-lg">add</span>
              <span>New Rule</span>
            </button>
          </div>
        </div>

        <!-- Bento Grid Metrics -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 lg:gap-6 mb-8 lg:mb-12">
          <AdminGrowthCard />

          <AdminStatCard 
            title="Total Verified Users" 
            value="842,019" 
            trend="+12%" 
            icon="groups" 
          />
          <AdminStatCard 
            title="Total Payments" 
            value="$1.2M" 
            trend="+8.4%" 
            icon="monetization_on" 
            borderColorClass="border-secondary" 
            iconColorClass="text-secondary"
          />
          <AdminStatCard 
            title="Active Sessions" 
            value="14,302" 
            trend="LIVE" 
            icon="sensors" 
            borderColorClass="border-tertiary" 
            iconColorClass="text-tertiary"
            trendColorClass="text-slate-500"
          />
          <AdminStatCard 
            title="Uptime Global" 
            value="99.98%" 
            trend="Stable" 
            icon="dns" 
            borderColorClass="border-outline" 
            iconColorClass="text-slate-400"
            trendColorClass="text-emerald-400 font-italic"
          />
        </div>

        <!-- Active Tournaments Management -->
        <section class="mb-8 lg:mb-12">
          <div class="flex items-center justify-between mb-6 lg:mb-8">
            <div class="flex items-center gap-3 lg:gap-4 min-w-0">
              <h3 class="text-xl lg:text-2xl font-headline font-bold text-slate-200 truncate">Active Tournaments</h3>
              <span class="px-2 py-0.5 rounded bg-primary/10 text-primary text-[10px] font-bold uppercase tracking-tighter shrink-0 hidden sm:inline-block">Live Management</span>
            </div>
            <div class="flex gap-2 shrink-0">
              <button class="p-2 rounded-lg bg-surface-container hover:bg-surface-container-high text-slate-400 transition-all">
                <span class="material-symbols-outlined text-xl">filter_list</span>
              </button>
              <button class="p-2 rounded-lg bg-surface-container hover:bg-surface-container-high text-slate-400 transition-all">
                <span class="material-symbols-outlined text-xl">more_horiz</span>
              </button>
            </div>
          </div>

          <div class="grid grid-cols-1 sm:grid-cols-2 xl:grid-cols-3 gap-4 lg:gap-6">
            <AdminTournamentCard 
              name="Neon Pulse League"
              id="TN-90234-ZY"
              prizePool="$25,000"
              status="Ongoing"
              image="https://lh3.googleusercontent.com/aida-public/AB6AXuBExV7J9FOZSckgLvg6D1j_c1AP55N_HUcvaRu3mL8Ihw5TSqAZ6HX_HfEcO9XC7YsE4a3Rhmqrt7EFN3bPCzSIxZeQSuFzxZsr91Y5YChTu_sl9AwCLJAc4mBiIjQ-KRInqEoKLzWall0DpUi4TNse_FcvB1CQYVu6YWx2qBplAT6OCx8fLh7uzvsTmIT1x8F9KaMJZodTjX4K9YslocM-XJPkT_wCrLLdxBUgbMj__R4I8xRAJFsC3de0QAq-UA7_7NX90k7IK9E"
              participants="+2.4k"
              actionIcon="pause"
            />
            <AdminTournamentCard 
              name="Shadow Realm Invites"
              id="TN-90235-ZY"
              prizePool="$5,000"
              status="Draft"
              image="https://lh3.googleusercontent.com/aida-public/AB6AXuBSpoimBEr8V8KMTD6nbpTTB1xPcHPlUCu_rSfPYu9m1gNJI_SqGVT2mAc-eQD81stI-hqYhwFbZF5L7bq6jQPkolWW_xJYJm_-lW03Qqx8DJXU3bfCpFG85VjI0RyamNZTxGYkuWbMP8Ro7s7zEOgfRzuHn6bjaEicxIUsBqRSuc_28mAj4aP59HrKQPUIguMZ3b2H2Mzh2mmOWvRRJEHyM8BhWl_4KrUr2465CIKc0mPYCA_fXCATmWLmQQDBoRuVnr1PXttE4Xu"
              participants="Invite Only"
              statusClass="text-secondary"
              actionIcon="play_arrow"
              actionClass="text-primary"
            />
            <AdminTournamentCard 
              name="Zenith Masters Cup"
              id="TN-90236-ZY"
              prizePool="$50,000"
              status="Ending Soon"
              image="https://lh3.googleusercontent.com/aida-public/AB6AXuDU_9MLLPAWVAmB9xbLCg_eaRUkbAZcM9VcaXtjmPV5KY4ubmdVVx0gLmBfJCJ96mqpxYfxiGa5GN_DHsFFntccY7xJEJnCg-ptm5IOhv7MLfYelTMBs0HCZquTy8dlAm2wsg2kk_nJt-KcV1w5wh0PJUWW7VXS26BWSwLG6pd_75izNILV4h6ejHDoT2ou4KIPzEr_5YDFuOfPne6MWcs6X7KD5ppAsofyKCqGLjEK9FIE4CaE123tmZgj-TKZFMW10ipttOnZ3-w"
              participants="+12"
              statusClass="text-tertiary"
              actionIcon="workspace_premium"
              actionClass="text-secondary"
            />
          </div>
        </section>

        <!-- Bottom Section: Logs & Activity -->
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-4 lg:gap-8">
          <AdminAuditLogs />
          <AdminSecurityLevel />
        </div>
      </div>

      <AdminFooter />
    </main>
  </div>
</template>

<style scoped>
.glass-panel {
  background: rgba(50, 49, 81, 0.6);
  backdrop-filter: blur(20px);
}
</style>
