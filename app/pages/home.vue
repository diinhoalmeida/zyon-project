<script setup lang="ts">
useHead({
  title: 'Zyon | League of Legends',
  bodyAttrs: {
    class: 'bg-[#10102e] text-[#e2dfff] font-["Space_Grotesk"]'
  }
})

const topCharacters = [
  { id: 1, name: 'Yasuo', winrate: '58%', games: 150, image: 'https://ddragon.leagueoflegends.com/cdn/img/champion/loading/Yasuo_0.jpg', bg: 'from-primary to-primary-container' },
  { id: 2, name: 'Zed', winrate: '56%', games: 315, image: 'https://ddragon.leagueoflegends.com/cdn/img/champion/loading/Zed_0.jpg', bg: 'from-amber-400 to-amber-600' },
  { id: 3, name: 'Ahri', winrate: '64%', games: 187, image: 'https://ddragon.leagueoflegends.com/cdn/img/champion/loading/Ahri_0.jpg', bg: 'from-rose-500 to-rose-700' }
]

const chatMessages = [
  { id: 1, name: 'Jessy Pinkman', time: '12:30', text: 'Wow, man, that\'s a great shot on the dribble!', avatar: 'https://i.pravatar.cc/150?u=1' },
  { id: 2, name: 'SweetHoney (4)', time: '10:25', text: 'Hey, how you doing? Shall we play?', avatar: 'https://i.pravatar.cc/150?u=2' },
  { id: 3, name: 'Cuticlecus (2)', time: '10:20', text: 'Hey dude! I got myself a new char! Go play, I\'ll show everyone!!', avatar: 'https://i.pravatar.cc/150?u=3' },
  { id: 4, name: 'Alborosia (8)', time: '10:05', text: 'you know what he did? ahhh', avatar: 'https://i.pravatar.cc/150?u=4' },
  { id: 5, name: 'Pinkydinky', time: '10:25', text: 'It\'s so boring to sit and fill out forms. Shall we play in half an hour?', avatar: 'https://i.pravatar.cc/150?u=5' },
  { id: 6, name: 'Naruto (3)', time: '10:00', text: 'Paula and I are going to play now. Are you with us?', avatar: 'https://i.pravatar.cc/150?u=6' }
]
</script>

<template>
  <div class="dark min-h-screen bg-[#10102e] text-[#e2dfff] font-['Inter']">
    <AdminSidebar />
    <AdminHeader />

    <main class="min-h-screen transition-[padding] duration-300 lg:pl-[280px] pt-[72px]">
      
      <div class="px-4 sm:px-6 lg:px-8 py-8 max-w-[1600px] mx-auto flex flex-col xl:flex-row gap-8">
        
        <!-- Left Main Context (Stats & Games) -->
        <div class="flex-1 space-y-10 min-w-0">
          
          <!-- Hero Section -->
          <section class="relative w-full h-[280px] bg-surface-container rounded-[2rem] overflow-hidden flex items-center p-8 md:p-12 shadow-2xl border border-white/5">
            <div class="relative z-20 max-w-sm">
              <h1 class="text-3xl md:text-[44px] font-black text-white uppercase tracking-wider mb-2 font-headline drop-shadow-xl leading-tight">League of Legends</h1>
              <p class="text-slate-300 text-[13px] md:text-sm mb-6 leading-relaxed max-w-[280px]">Destrua as torres adversárias e alcance a vitória na arena competitiva mais jogada do planeta.</p>
              <button class="bg-primary text-white font-bold px-10 py-3.5 rounded-full hover:bg-primary-container transition-all hover:-translate-y-1 shadow-[0_10px_20px_-10px_rgba(69,22,205,0.7)] tracking-widest text-[11px] uppercase">
                Jogar
              </button>
            </div>
            
            <!-- Hero Image Cutout -->
            <div class="absolute right-0 bottom-0 h-full w-[65%] pointer-events-none">
              <!-- Masking trick to fade the left edge of the banner image -->
              <div class="absolute inset-0 bg-gradient-to-r from-surface-container via-surface-container/20 to-transparent z-10 w-1/4"></div>
              <img src="https://ddragon.leagueoflegends.com/cdn/img/champion/splash/Jinx_0.jpg" class="h-full w-full object-cover object-[center_20%] opacity-80" />
            </div>
          </section>

          <!-- Top Characters -->
          <section>
            <h2 class="text-lg font-bold text-white mb-6 font-headline tracking-wide">Top Characters</h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
              
              <div 
                v-for="char in topCharacters" 
                :key="char.id"
                :class="['relative rounded-3xl p-6 h-[180px] overflow-hidden group hover:-translate-y-1 transition-all duration-300 shadow-xl', 'bg-gradient-to-br ' + char.bg]"
              >
                <div class="relative z-10 mt-10">
                  <h3 class="text-2xl text-white font-black drop-shadow-md mb-2 font-headline">{{ char.name }}</h3>
                  <div class="flex gap-5">
                    <div>
                      <span class="text-white font-bold text-lg block leading-none">{{ char.winrate }}</span>
                      <span class="text-[10px] text-white/80 uppercase font-medium">Win rate</span>
                    </div>
                    <div>
                      <span class="text-white font-bold text-lg block leading-none">{{ char.games }}</span>
                      <span class="text-[10px] text-white/80 uppercase font-medium">Games</span>
                    </div>
                  </div>
                </div>
                <!-- Character Image with smooth fade mask on the left edge -->
                <img :src="char.image" class="absolute right-0 top-0 h-full w-[55%] object-cover object-[center_10%] opacity-80 group-hover:opacity-100 group-hover:scale-110 transition-all duration-500" style="-webkit-mask-image: linear-gradient(to right, transparent 0%, black 45%); mask-image: linear-gradient(to right, transparent 0%, black 45%);" />
              </div>

            </div>
          </section>

          <!-- Stats Section -->
          <section>
            <h2 class="text-lg font-bold text-white mb-6 font-headline tracking-wide">Stats</h2>
            
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
              <!-- Radar Chart Placeholder -->
              <div class="col-span-1 bg-surface-container/50 rounded-[2rem] p-6 border border-white/5 flex items-center justify-center relative">
                <svg viewBox="0 0 100 100" class="w-full max-w-[200px] h-auto drop-shadow-xl text-slate-700">
                  <!-- Radar net -->
                  <polygon points="50,5 95,38 78,95 22,95 5,38" fill="none" stroke="currentColor" stroke-width="1" />
                  <polygon points="50,28 72,44 64,72 36,72 28,44" fill="none" stroke="currentColor" stroke-width="1" />
                  <line x1="50" y1="50" x2="50" y2="5" stroke="currentColor" stroke-width="1" />
                  <line x1="50" y1="50" x2="95" y2="38" stroke="currentColor" stroke-width="1" />
                  <line x1="50" y1="50" x2="78" y2="95" stroke="currentColor" stroke-width="1" />
                  <line x1="50" y1="50" x2="22" y2="95" stroke="currentColor" stroke-width="1" />
                  <line x1="50" y1="50" x2="5" y2="38" stroke="currentColor" stroke-width="1" />
                  
                  <!-- Radar Data shape (Blue/Primary) -->
                  <polygon points="50,15 80,45 60,65 30,90 20,40" fill="rgba(69,22,205,0.7)" stroke="#c9bfff" stroke-width="1.5" />
                </svg>
                
                <!-- Mock Labels -->
                <span class="absolute top-4 left-1/2 -translate-x-1/2 text-[9px] font-bold text-slate-400">Total Kills<br/><span class="text-white">430</span></span>
                <span class="absolute bottom-6 left-6 text-[9px] font-bold text-slate-400">Assists<br/><span class="text-white">120</span></span>
                <span class="absolute bottom-6 right-6 text-[9px] font-bold text-slate-400">Farming<br/><span class="text-white">32</span></span>
              </div>

              <!-- Line Chart Placeholder -->
              <div class="col-span-2 bg-surface-container/50 rounded-[2rem] p-6 border border-white/5">
                <div class="flex items-center gap-6 mb-6 text-xs text-slate-500 font-bold uppercase tracking-wider">
                  <button class="text-white relative after:absolute after:-bottom-2 after:left-0 after:w-full after:h-0.5 after:bg-primary after:rounded-full">Online</button>
                  <button class="hover:text-amber-400 transition-colors">Distances</button>
                  <button class="hover:text-amber-400 transition-colors">Best Played</button>
                </div>
                
                <div class="relative w-full h-[150px] mt-4">
                  <svg viewBox="0 0 400 100" class="w-full h-full preserveAspectRatio='none'">
                    <defs>
                      <linearGradient id="lineGrad" x1="0" y1="0" x2="0" y2="1">
                        <stop offset="0%" stop-color="rgba(251, 191, 36, 0.2)" /> <!-- Amber gradient -->
                        <stop offset="100%" stop-color="rgba(251, 191, 36, 0)" />
                      </linearGradient>
                    </defs>
                    <path d="M0,80 C40,90 60,40 100,50 C140,60 170,90 210,70 C250,50 280,60 320,30 C360,10 380,50 400,20 L400,100 L0,100 Z" fill="url(#lineGrad)" />
                    <path d="M0,80 C40,90 60,40 100,50 C140,60 170,90 210,70 C250,50 280,60 320,30 C360,10 380,50 400,20" fill="none" class="stroke-amber-400" stroke-width="2.5" />
                  </svg>
                  
                  <!-- Bottom Mock Axis Labels -->
                  <div class="absolute -bottom-4 left-0 w-full flex justify-between text-[9px] text-slate-600 font-bold px-2">
                    <span>Jan</span><span>Feb</span><span>Mar</span><span>Apr</span><span>May</span><span>Jun</span><span>Jul</span><span>Aug</span><span>Sep</span><span>Oct</span><span>Nov</span><span>Dec</span>
                  </div>
                </div>
              </div>
            </div>
            
          </section>

        </div>

        <!-- Chat Sidebar Right -->
        <div class="w-full xl:w-[320px] shrink-0">
          <div class="bg-surface-container rounded-[2rem] p-6 h-[calc(100vh-120px)] sticky top-[92px] flex flex-col border border-white/5 shadow-2xl">
            
            <div class="flex justify-between items-center mb-6">
              <h3 class="text-white font-bold font-headline tracking-wide">Mezzaliner's</h3>
              <span class="flex items-center gap-1.5 text-slate-400 text-[11px] font-bold">
                <span class="material-symbols-outlined text-sm">group</span> 125
              </span>
            </div>

            <div class="flex-1 overflow-y-auto no-scrollbar space-y-5 relative">
              <NuxtLink 
                v-for="msg in chatMessages" 
                :key="msg.id"
                to="/profile"
                class="flex items-start gap-4 group cursor-pointer"
              >
                <div class="relative shrink-0">
                  <img :src="msg.avatar" class="w-10 h-10 rounded-[0.8rem] bg-[#1d1c3a] object-cover ring-2 ring-transparent group-hover:ring-primary transition-all" />
                  <div class="absolute bottom-0 right-0 w-3 h-3 bg-emerald-400 rounded-full border-2 border-surface-container translate-x-1/4 translate-y-1/4"></div>
                </div>
                
                <div class="flex-1 min-w-0">
                  <div class="flex justify-between items-baseline mb-0.5">
                    <h4 class="text-[13px] font-bold text-white truncate">{{ msg.name }}</h4>
                    <span class="text-[10px] text-slate-500 font-medium shrink-0 ml-2">{{ msg.time }}</span>
                  </div>
                  <p class="text-[11px] text-slate-400 leading-snug line-clamp-2">{{ msg.text }}</p>
                </div>
              </NuxtLink>
            </div>

            <!-- Chat Input -->
            <div class="mt-4 shrink-0 relative">
              <input 
                type="text" 
                placeholder="Start writing here..." 
                class="w-full bg-[#10102e] border border-white/10 rounded-2xl pl-4 pr-12 py-3.5 text-xs text-white placeholder:text-slate-500 focus:ring-1 focus:ring-primary outline-none transition-all"
              />
              <button class="absolute right-2 top-1/2 -translate-y-1/2 w-9 h-9 bg-primary text-white rounded-xl flex items-center justify-center hover:bg-primary-container transition-colors shadow-lg shadow-primary/30 outline-none">
                <span class="material-symbols-outlined text-[18px]">send</span>
              </button>
            </div>
            
          </div>
        </div>

      </div>
    </main>
  </div>
</template>

<style scoped>
.font-headline {
  font-family: 'Space Grotesk', sans-serif;
}
</style>
