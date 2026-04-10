<template>
  <section class="relative min-h-screen flex items-center pt-20 overflow-hidden">
    <!-- Background Decorative Elements -->
    <div class="absolute top-0 right-0 w-2/3 h-full opacity-40 pointer-events-none translate-x-1/4">
      <img 
        alt="Futuristic landscape" 
        class="w-full h-full object-cover" 
        src="https://lh3.googleusercontent.com/aida-public/AB6AXuC9MPYgnSstteOvbfry1C7-EqSb4JLyqO75svVFRDpe8GA06uyoBdCZsZkH5DeLDV4PLYOWpRGLo3uUq5ZPCHQfUV9atM7sr4zSjTpx6aDdr1rlOUHSB6kIe5gfa0E7b12yKrABkMfzA-EMxnPt6_WigkWBPTZOzD_beLHZLt0LqEs4W_f17Jq0jR-ONJZ8nPe88CgoEBt_9RVtNcKCUCy_il7G2CM_Qxn1WcdMHOLh7oaLdDH-ThNPzWCqm46q5INCSBOtGu8yjK4"
      />
    </div>

    <!-- Radial Gradient Overlay -->
    <div class="absolute inset-0 bg-gradient-to-r from-surface via-surface/90 to-transparent z-10"></div>

    <div class="container mx-auto px-8 relative z-20 flex flex-col items-start gap-8 max-w-screen-2xl">
      <div class="space-y-4 max-w-3xl">
        <span class="inline-block uppercase tracking-[0.2em] text-secondary font-semibold headline-font bg-surface-container-high px-4 py-1 rounded-full text-xs">
          A Arena dos Gamers Competitivos
        </span>
        <h1 class="text-6xl md:text-8xl headline-font font-bold leading-[0.9] tracking-tighter text-glow">
          Sua Habilidade <br/> 
          Transformada em <br/> 
          <span class="text-primary">Resultados Reais</span>
        </h1>
        <p class="text-xl text-on-surface-variant leading-relaxed max-w-xl font-body mt-6">
          A plataforma definitiva para quem leva o jogo a sério. Participe de torneios, vença desafios e monetize seu desempenho em cada partida.
        </p>
      </div>

      <div class="flex flex-wrap gap-6 mt-4">
        <button class="primary-gradient text-on-primary font-bold px-10 py-5 rounded-full text-lg headline-font tracking-wide scale-100 hover:scale-105 active:scale-95 transition-all shadow-[0_40px_60px_-10px_rgba(69,22,205,0.4)] flex items-center gap-3">
          Entrar na Arena
          <span class="material-symbols-outlined">account_balance_wallet</span>
        </button>
        <button class="bg-transparent border-[1.5px] border-outline-variant/30 text-secondary font-bold px-10 py-5 rounded-full text-lg headline-font tracking-wide hover:bg-surface-container-high transition-all flex items-center gap-3">
          Explorar Torneios
          <span class="material-symbols-outlined">arrow_forward</span>
        </button>
      </div>

      <!-- Live Metrics (Asymmetric Bento Element) -->
      <div class="mt-20 grid grid-cols-2 md:grid-cols-4 gap-12 border-l border-outline-variant/20 pl-8">
        <div>
          <div class="text-3xl font-bold headline-font">250K+</div>
          <div class="text-xs uppercase tracking-widest text-slate-500 mt-1">Jogadores Ativos</div>
        </div>
        <div>
          <div class="text-3xl font-bold headline-font">42</div>
          <div class="text-xs uppercase tracking-widest text-slate-500 mt-1">Estúdios de Jogos</div>
        </div>
        <div>
          <div class="text-3xl font-bold headline-font">$1.2M</div>
          <div class="text-xs uppercase tracking-widest text-slate-500 mt-1">Recompensas Pagas</div>
        </div>
        <div>
          <div class="text-3xl font-bold headline-font">0.2s</div>
          <div class="text-xs uppercase tracking-widest text-slate-500 mt-1">Latência Média</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// Hero logic can be added here
</script>
