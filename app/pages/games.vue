<script setup lang="ts">
useHead({
  title: 'Catálogo de Jogos | Zyon Arena',
  meta: [
    { name: 'description', content: 'Explore os jogos suportados pela Zyon. Dispute torneios de League of Legends e prepare-se para Valorant, CS2 e muito mais.' }
  ]
})

const games = [
  {
    id: 'lol',
    name: 'League of Legends',
    genre: 'MOBA',
    image: '/games/lol.png',
    status: 'active',
    statusLabel: 'Disponível',
    description: 'Domine Summoner\'s Rift e conquiste premiações em cada partida.',
    link: '/tournament-area'
  },
  {
    id: 'valorant',
    name: 'Valorant',
    genre: 'FPS Tático',
    image: '/games/valorant.png',
    status: 'upcoming',
    statusLabel: 'Em Breve',
    description: 'Onde o seu skillcap encontra a precisão tática.',
    link: '#'
  },
  {
    id: 'cs2',
    name: 'Counter-Strike 2',
    genre: 'FPS Tático',
    image: '/games/cs2.png',
    status: 'upcoming',
    statusLabel: 'Em Breve',
    description: 'A evolução do FPS competitivo está chegando na Zyon.',
    link: '#'
  },
  {
    id: 'warzone',
    name: 'COD: Warzone',
    genre: 'Battle Royale',
    image: '/games/warzone.png',
    status: 'upcoming',
    statusLabel: 'Em Breve',
    description: 'Sobreviva, domine e lucre no campo de batalha definitivo.',
    link: '#'
  }
]
</script>

<template>
  <div class="bg-surface text-on-surface min-h-screen font-body selection:bg-primary selection:text-on-primary">
    <LandingNav />

    <main class="pt-32 pb-24 px-8">
      <div class="container mx-auto max-w-screen-2xl">
        <!-- Header -->
        <header class="mb-16">
          <h1 class="text-4xl md:text-6xl headline-font font-bold mb-4 tracking-tighter">
            Selecione seu <span class="text-primary italic">Campo de Batalha</span>
          </h1>
          <p class="text-slate-400 text-lg max-w-2xl font-body">
            Conecte seus jogos favoritos e monetize seu desempenho. Novos títulos são validados e adicionados regularmente.
          </p>
        </header>

        <!-- Games Grid -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
          <div 
            v-for="game in games" 
            :key="game.id"
            :class="[
              'group relative rounded-3xl overflow-hidden bg-surface-container border transition-all duration-500',
              game.status === 'active' 
                ? 'border-primary/20 hover:border-primary/50 shadow-2xl shadow-primary/5' 
                : 'border-outline-variant/10 opacity-60 grayscale cursor-not-allowed'
            ]"
          >
            <!-- Game Image -->
            <div class="aspect-[3/4] overflow-hidden relative">
              <img 
                :src="game.image" 
                :alt="game.name"
                class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-surface-container-lowest via-transparent to-transparent"></div>
              
              <!-- Status Badge -->
              <div class="absolute top-6 right-6">
                <span :class="[
                  'px-3 py-1 rounded-full headline-font font-bold text-[10px] uppercase tracking-widest backdrop-blur-md',
                  game.status === 'active' 
                    ? 'bg-primary/90 text-on-primary' 
                    : 'bg-surface-container-highest text-slate-400'
                ]">
                  {{ game.statusLabel }}
                </span>
              </div>
            </div>

            <!-- Game Info -->
            <div class="p-8">
              <div class="text-[10px] font-bold text-primary headline-font uppercase tracking-widest mb-2">
                {{ game.genre }}
              </div>
              <h3 class="text-2xl font-bold headline-font mb-4 tracking-tight">
                {{ game.name }}
              </h3>
              <p class="text-slate-400 text-sm leading-relaxed mb-8 line-clamp-2">
                {{ game.description }}
              </p>

              <!-- Action Button -->
              <NuxtLink 
                :to="game.link"
                :class="[
                  'w-full py-4 rounded-xl headline-font font-bold text-sm text-center transition-all flex items-center justify-center gap-2',
                  game.status === 'active' 
                    ? 'primary-gradient text-on-primary shadow-lg shadow-primary/20' 
                    : 'bg-surface-container-high text-slate-500 pointer-events-none'
                ]"
              >
                {{ game.status === 'active' ? 'Entrar na Arena' : 'Em Breve' }}
                <span v-if="game.status === 'active'" class="material-symbols-outlined text-base">trending_flat</span>
              </NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </main>

    <LandingFooter />
  </div>
</template>

<style scoped>
.grayscale {
  filter: grayscale(1);
}
</style>
