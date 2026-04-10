<script setup lang="ts">
// Shared state with Sidebar
const isSidebarOpen = useState('adminSidebarOpen', () => false)

function toggleSidebar() {
  isSidebarOpen.value = !isSidebarOpen.value
}
</script>

<template>
  <header class="fixed top-0 left-0 right-0 z-40 h-[72px] bg-[#10102e]/95 backdrop-blur-xl shadow-lg border-b border-outline-variant/10 flex items-center">
    <div class="flex justify-between items-center px-6 w-full font-['Space_Grotesk'] text-sm">
      
      <!-- Left Section: Branding -->
      <div class="flex items-center gap-3">
        <div class="w-8 h-8 rounded-xl bg-linear-to-br from-primary to-primary-container flex items-center justify-center text-on-primary shadow-sm">
          <span class="material-symbols-outlined text-lg" style="font-variation-settings: 'FILL' 1;">bolt</span>
        </div>
        <div class="hidden sm:block">
          <span class="font-black text-white text-[15px] leading-none uppercase tracking-widest block">Zyon</span>
        </div>
      </div>

      <!-- Middle Section: Search Bar -->
      <div class="relative group flex-1 max-w-88 mx-auto hidden md:block">
        <span class="material-symbols-outlined absolute left-4 top-1/2 -translate-y-1/2 text-slate-400 group-focus-within:text-primary transition-colors text-lg">search</span>
        <input class="w-full bg-surface-container/80 border border-outline-variant/10 rounded-full pl-11 pr-4 py-2.5 focus:ring-1 focus:ring-primary focus:border-primary text-[13px] tracking-normal normal-case text-white placeholder:text-slate-500 transition-all outline-none" placeholder="Pesquisar torneios..." type="text"/>
      </div>

      <!-- Right Section: Actions & Profile -->
      <div class="flex items-center gap-5">
        
        <!-- Action Icons -->
        <div class="flex items-center gap-4 border-r border-outline-variant/10 pr-5">
          <button class="text-slate-400 hover:text-white transition-colors relative">
            <span class="material-symbols-outlined text-[20px]">chat</span>
          </button>
          <button class="text-slate-400 hover:text-white transition-colors relative">
            <span class="material-symbols-outlined text-[20px]">notifications</span>
            <span class="absolute -top-1 -right-1 w-2 h-2 bg-pink-500 rounded-full border border-[#12141D]"></span>
          </button>
        </div>

        <!-- Profile Section -->
        <NuxtLink to="/profile" class="flex items-center gap-3 hover:bg-surface-container p-1.5 rounded-xl transition-colors outline-none cursor-pointer border border-transparent hover:border-outline-variant/10">
          <img src="https://i.pravatar.cc/150?u=zyon_header" class="w-9 h-9 rounded-full border-2 border-primary object-cover" />
          <span class="text-xs font-bold text-white hidden sm:block font-headline tracking-wide">Player 1</span>
        </NuxtLink>

        <!-- Mobile Menu Toggle (Only visible under md) -->
        <button class="md:hidden text-slate-400" @click="toggleSidebar">
          <span class="material-symbols-outlined">menu</span>
        </button>
      </div>

    </div>
  </header>
</template>
