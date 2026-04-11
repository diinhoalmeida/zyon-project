<template>
  <nav class="fixed top-0 w-full z-50 bg-background/60 backdrop-blur-md shadow-[0_20px_40px_-5px_rgba(69,22,205,0.15)]">
    <div class="flex justify-between items-center px-8 py-4 max-w-screen-2xl mx-auto">
      <div class="text-2xl font-bold tracking-tighter text-primary headline-font">Zyon</div>
      
      <div class="hidden md:flex gap-8 headline-font text-sm tracking-widest uppercase items-center">
        <NuxtLink to="/games" class="text-slate-400 hover:text-primary transition-colors">Jogos</NuxtLink>
        <NuxtLink to="/tournaments" class="text-slate-400 hover:text-primary transition-colors">Torneios</NuxtLink>
        <NuxtLink to="/about" class="text-slate-400 hover:text-primary transition-colors">Sobre Nós</NuxtLink>
      </div>

      <div class="flex items-center gap-4">
        <button class="primary-gradient text-on-primary font-bold px-6 py-2.5 rounded-full text-sm headline-font tracking-wide scale-95 hover:scale-100 active:scale-90 transition-all shadow-[0_30px_40px_-5px_rgba(69,22,205,0.3)]">
          Entrar na Arena
        </button>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">
// Navigation logic can be added here
</script>
