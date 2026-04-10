<script setup lang="ts">
// Landing page assembly
useHead({
  title: 'Zyon | Sua Habilidade Vale Dinheiro',
  meta: [
    { name: 'description', content: 'A arena definitiva para gamers competitivos. Jogue, dispute torneios e monetize seu desempenho em cada partida no ecossistema Zyon.' }
  ]
})
</script>

<template>
  <div class="bg-surface text-on-surface selection:bg-primary selection:text-on-primary min-h-screen">
    <LandingNav />
    
    <main>
      <LandingHero />
      <LandingFeaturedGames />
      <LandingEcosystem />
    </main>

    <LandingFooter />
  </div>
</template>

<style scoped>
/* Any page-specific styles */
</style>
