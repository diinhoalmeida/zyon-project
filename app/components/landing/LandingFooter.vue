<template>
  <footer class="bg-surface w-full py-12 px-8 border-t border-outline-variant/10">
    <div class="max-w-screen-2xl mx-auto">
      <div class="flex flex-col md:flex-row justify-between items-start gap-12 mb-12">
        <div class="space-y-6">
          <div class="text-2xl font-black text-slate-300 headline-font">Zyon Kinetic</div>
          <p class="text-slate-500 max-w-sm font-body text-sm leading-relaxed">O destino principal para gamers competitivos e a elite dos ativos digitais.</p>
          <div class="flex gap-4">
            <a href="#" class="w-10 h-10 rounded-full bg-surface-container flex items-center justify-center hover:text-secondary transition-colors">
              <span class="material-symbols-outlined text-sm">public</span>
            </a>
            <a href="#" class="w-10 h-10 rounded-full bg-surface-container flex items-center justify-center hover:text-secondary transition-colors">
              <span class="material-symbols-outlined text-sm">chat</span>
            </a>
            <a href="#" class="w-10 h-10 rounded-full bg-surface-container flex items-center justify-center hover:text-secondary transition-colors">
              <span class="material-symbols-outlined text-sm">code</span>
            </a>
          </div>
        </div>

        <div class="grid grid-cols-2 md:grid-cols-3 gap-16">
          <div>
            <h5 class="text-primary headline-font text-xs uppercase tracking-widest mb-6 font-bold">Plataforma</h5>
            <ul class="space-y-4 font-body text-sm text-slate-500">
              <li><NuxtLink to="/games" class="hover:text-secondary transition-colors">Jogos</NuxtLink></li>
              <li><NuxtLink to="/tournaments" class="hover:text-secondary transition-colors">Torneios</NuxtLink></li>
              <li><NuxtLink to="/about" class="hover:text-secondary transition-colors">Sobre Nós</NuxtLink></li>
            </ul>
          </div>
          <div>
            <h5 class="text-primary headline-font text-xs uppercase tracking-widest mb-6 font-bold">Conectar</h5>
            <ul class="space-y-4 font-body text-sm text-slate-500">
              <li><NuxtLink to="#" class="hover:text-secondary transition-colors">Discord</NuxtLink></li>
              <li><NuxtLink to="#" class="hover:text-secondary transition-colors">Twitter</NuxtLink></li>
              <li><NuxtLink to="#" class="hover:text-secondary transition-colors">Comunidade</NuxtLink></li>
              <li><NuxtLink to="#" class="hover:text-secondary transition-colors">Suporte</NuxtLink></li>
            </ul>
          </div>
          <div class="col-span-2 md:col-span-1">
            <h5 class="text-primary headline-font text-xs uppercase tracking-widest mb-6 font-bold">Legal</h5>
            <ul class="space-y-4 font-body text-sm text-slate-500">
              <li><NuxtLink to="#" class="hover:text-secondary transition-colors">Termos</NuxtLink></li>
              <li><NuxtLink to="#" class="hover:text-secondary transition-colors">Privacidade</NuxtLink></li>
              <li><NuxtLink to="#" class="hover:text-secondary transition-colors">Cookies</NuxtLink></li>
            </ul>
          </div>
        </div>
      </div>

      <div class="pt-8 border-t border-outline-variant/10 flex flex-col md:flex-row justify-between items-center gap-6">
        <div class="font-body text-xs text-slate-500">© 2024 Zyon Kinetic. Todos os direitos reservados.</div>
        <div class="flex items-center gap-2">
          <div class="w-2 h-2 rounded-full bg-green-500 animate-pulse"></div>
          <span class="text-[10px] text-slate-500 uppercase tracking-widest">Servidores Online</span>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
// Footer logic
</script>
