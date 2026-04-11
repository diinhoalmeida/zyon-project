<script setup lang="ts">
useHead({
  title: 'Sobre a Zyon | A Revolução do Gaming Competitivo',
  meta: [
    { name: 'description', content: 'Conheça a missão da Zyon: empoderar gamers através da monetização de habilidade e integridade competitiva.' }
  ]
})
</script>

<template>
  <div class="bg-surface text-on-surface min-h-screen font-body selection:bg-primary selection:text-on-primary">
    <LandingNav />

    <main class="pt-32 pb-24 px-8">
      <div class="container mx-auto max-w-screen-xl">
        <!-- Hero Section -->
        <section class="mb-24 text-center">
          <span class="inline-block uppercase tracking-[0.3em] text-primary font-bold headline-font text-xs mb-4">Nossa Missão</span>
          <h1 class="text-5xl md:text-7xl headline-font font-bold mb-8 tracking-tighter">
            Transformando Paixão em <br />
            <span class="text-primary italic">Resultados</span>
          </h1>
          <p class="text-xl text-slate-400 max-w-3xl mx-auto leading-relaxed">
            A Zyon nasceu da inconformidade com um mercado onde gamers dedicam milhares de horas sem retorno proporcional. Nossa plataforma é o ponto de encontro entre a habilidade bruta e a recompensa justa.
          </p>
        </section>

        <!-- Values Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-12 mb-32">
          <div class="glass-panel p-12 rounded-3xl border border-outline-variant/10 relative overflow-hidden group">
            <div class="absolute top-0 right-0 p-8 opacity-10 group-hover:scale-110 transition-transform">
              <span class="material-symbols-outlined text-8xl">military_tech</span>
            </div>
            <h2 class="text-3xl font-bold headline-font mb-6">Integridade Acima de Tudo</h2>
            <p class="text-slate-400 text-lg leading-relaxed">
              Damos o máximo de transparência e foco na validação de resultados. Nossa plataforma é construída para que a competitividade seja levada a sério e o mérito real seja sempre recompensado.
            </p>
          </div>

          <div class="glass-panel p-12 rounded-3xl border border-outline-variant/10 relative overflow-hidden group">
            <div class="absolute top-0 right-0 p-8 opacity-10 group-hover:scale-110 transition-transform">
              <span class="material-symbols-outlined text-8xl">payments</span>
            </div>
            <h2 class="text-3xl font-bold headline-font mb-6">Monetização de Skill</h2>
            <p class="text-slate-400 text-lg leading-relaxed">
              Acreditamos que o desempenho deve ser recompensado. Seja em torneios globais ou desafios 1v1, sua evolução como jogador reflete diretamente no seu saldo.
            </p>
          </div>
        </div>

        <!-- Vision Section -->
        <section class="grid grid-cols-1 lg:grid-cols-2 gap-20 items-center mb-20 lg:mb-32">
          <div class="relative">
            <div class="aspect-square rounded-full border-[1.5px] border-primary/20 absolute -inset-10 animate-spin-slow"></div>
            <img 
              src="/zyon_vision_section.png" 
              alt="Futuristic Zyon Core" 
              class="rounded-3xl shadow-2xl relative z-10 w-full object-cover aspect-video border border-primary/20"
            />
          </div>
          <div class="space-y-8">
            <h2 class="text-4xl font-bold headline-font">O Futuro é <br/> Competitivo</h2>
            <p class="text-slate-400 leading-relaxed text-lg">
              Não somos apenas mais uma plataforma de jogos. Somos o ecossistema que profissionaliza o amador e escala o profissional. No coração da Zyon está a nossa comunidade: vocês, que fazem de cada partida um espetáculo de habilidade.
            </p>
            <NuxtLink to="/tournaments" class="primary-gradient text-on-primary font-bold px-8 py-4 rounded-full inline-flex items-center gap-3 headline-font hover:scale-105 transition-transform">
              Entrar na Arena
              <span class="material-symbols-outlined">trending_flat</span>
            </NuxtLink>
          </div>
        </section>
      </div>
    </main>

    <LandingFooter />
  </div>
</template>

<style scoped>
.animate-spin-slow {
  animation: spin 20s linear infinite;
}

@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
</style>
