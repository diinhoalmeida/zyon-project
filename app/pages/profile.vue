<script setup lang="ts">
const route = useRoute()

useHead({
  title: 'Zyon | Perfil do Jogador',
  bodyAttrs: {
    class: 'bg-[#10102e] text-[#e2dfff] font-["Space_Grotesk"]'
  }
})

const user = {
  name: 'Empre55ive',
  joined: 'Abril 2024',
  avatar: 'https://i.pravatar.cc/150?u=zyon_profile',
  banner: 'https://images.contentstack.io/v3/assets/blt7311d63b5823f097/blt90666a6a73c1555a/6078ced0145fa30f40d7c71f/Empyrean_2022_Banner.jpg',
  stats: {
    visualizações: '930k',
    clipes: '82',
    seguidores: '5.7K',
    seguindo: '24'
  }
}

const activeTab = ref('Feed')
const tabs = ['Feed', 'Favoritos', 'Marcados']

const posts = [
  {
    id: 1,
    type: 'clip',
    title: 'Pentakill Insano de Yasuo na Arena!',
    views: '1,459',
    thumbnail: 'https://ddragon.leagueoflegends.com/cdn/img/champion/splash/Yasuo_0.jpg',
    tags: ['#LeagueOfLegends', '#Yasuo', '#Pentakill'],
    date: '2 horas atrás'
  },
  {
    id: 2,
    type: 'tournament',
    title: 'Estou participando do Torneio Blitz Cup S2!',
    tournamentName: 'Blitz Cup - Season 2',
    prize: '$500 USD',
    date: 'Ontem',
    image: 'https://images.contentstack.io/v3/assets/blt7311d63b5823f097/blt5659837926b48722/616dedf15a9f2913f097486e/Viego_Splash_0.jpg'
  }
]

const competitiveStats = {
  rank: 'Diamante III',
  rankIcon: 'https://static.wikia.nocookie.net/leagueoflegends/images/9/96/Season_2023_-_Diamond_1.png',
  winRate: '66.9%',
  winLoss: '86W 12L'
}

const topChampion = {
  name: 'Yasuo',
  image: 'https://ddragon.leagueoflegends.com/cdn/img/champion/loading/Yasuo_0.jpg',
  winRate: '62.2%',
  kdRatio: '1.24',
  avgDmg: '136.5k'
}

const leaderboard = [
  { rank: 1, name: 'Simmycool', points: 8566, avatar: 'https://i.pravatar.cc/150?u=s1' },
  { rank: 2, name: 'NarcJacobs', points: 8300, avatar: 'https://i.pravatar.cc/150?u=s2' },
  { rank: 3, name: 'Empre55ive', points: 8150, avatar: 'https://i.pravatar.cc/150?u=zyon_profile', current: true },
]
</script>

<template>
  <div class="dark min-h-screen bg-background text-on-background font-['Inter']">
    <AdminSidebar />
    <AdminHeader />

    <main class="min-h-screen transition-[padding] duration-300 lg:pl-[280px] pt-[72px]">
      
      <div class="px-4 md:px-8 py-8 xl:py-12 max-w-[1400px] mx-auto space-y-10">
        
        <!-- Profile Banner Card -->
        <div class="bg-surface-container rounded-3xl overflow-hidden flex flex-col shadow-2xl relative">
          <!-- Top section (Image + Info) -->
          <div class="relative h-[220px] md:h-[260px] w-full">
            <img :src="user.banner" class="absolute inset-0 w-full h-full object-cover opacity-60" />
            <div class="absolute inset-0 bg-gradient-to-r from-surface-container via-surface-container/60 to-transparent"></div>
            <div class="absolute inset-0 bg-gradient-to-t from-surface-container via-transparent to-transparent"></div>
            
            <!-- Top Right: Friends & Socials -->
            <div class="absolute top-6 right-6 flex flex-col items-end gap-3 z-20">
              <div class="flex items-center gap-3 bg-black/60 backdrop-blur-md rounded-full pl-2 pr-4 py-1.5 border border-white/5">
                <div class="flex -space-x-2">
                   <img src="https://i.pravatar.cc/150?u=s1" class="w-6 h-6 rounded-full border border-black" />
                   <img src="https://i.pravatar.cc/150?u=s2" class="w-6 h-6 rounded-full border border-black" />
                   <img src="https://i.pravatar.cc/150?u=s3" class="w-6 h-6 rounded-full border border-black" />
                </div>
                <span class="text-[10px] text-white font-medium">You and <strong>{{ user.name }}</strong> also follow <strong>3 others</strong></span>
                <span class="material-symbols-outlined text-slate-400 text-sm ml-2">more_vert</span>
              </div>
              <button class="bg-surface-container-high hover:bg-white/10 text-white font-medium text-[10px] px-5 py-2 rounded-full border border-white/5 transition-colors">
                Copy Profile link
              </button>
              <div class="flex gap-2">
                <button class="w-8 h-8 rounded-[0.6rem] bg-[#5865F2] hover:bg-[#5865F2]/80 flex items-center justify-center transition-colors">
                   <span class="font-bold text-white text-xs">d</span>
                </button>
                <button class="w-8 h-8 rounded-[0.6rem] bg-[#1DA1F2] hover:bg-[#1DA1F2]/80 flex items-center justify-center transition-colors">
                   <span class="font-bold text-white text-xs">t</span>
                </button>
                <button class="w-8 h-8 rounded-[0.6rem] bg-[#E1306C] hover:bg-[#E1306C]/80 flex items-center justify-center transition-colors">
                   <span class="font-bold text-white text-xs">i</span>
                </button>
                <button class="w-8 h-8 rounded-[0.6rem] bg-[#9146FF] hover:bg-[#9146FF]/80 flex items-center justify-center transition-colors">
                   <span class="font-bold text-white text-xs">tw</span>
                </button>
              </div>
            </div>

            <!-- Bottom Left: Avatar & User details -->
            <div class="absolute bottom-6 left-8 flex items-center gap-6 z-20">
              <div class="relative">
                <div class="w-[100px] h-[100px] rounded-3xl overflow-hidden border-2 border-primary group cursor-pointer shadow-xl relative z-10">
                  <img :src="user.avatar" class="w-full h-full object-cover" />
                </div>
              </div>
              <div class="flex flex-col justify-center">
                <h1 class="text-[26px] font-bold text-white tracking-tight leading-tight">{{ user.name }}</h1>
                <p class="text-[11px] text-slate-400 mb-4 font-medium">Joined {{ user.joined }}</p>
                <div class="flex gap-3">
                  <button class="bg-amber-400 text-black font-bold px-6 py-2 rounded-xl hover:bg-amber-300 transition-colors flex items-center justify-center gap-2 text-[11px] min-w-[100px]">
                    <span class="material-symbols-outlined text-sm">person_add</span> Follow
                  </button>
                  <button class="bg-surface-container-highest text-white font-bold px-6 py-2 rounded-xl hover:bg-white/10 transition-colors flex items-center justify-center gap-2 text-[11px] min-w-[100px] border border-white/5">
                    <span class="material-symbols-outlined text-sm">chat_bubble_outline</span> Message
                  </button>
                </div>
              </div>
            </div>
          </div>

          <!-- Bottom Stats section of Banner -->
          <div class="bg-background px-8 py-5 flex flex-col lg:flex-row items-center justify-between gap-6 border-t border-white/[0.02]">
            <div class="flex items-center gap-10">
              <div class="group cursor-pointer text-center relative flex flex-col items-center">
                <div class="absolute -right-5 top-1/2 -translate-y-1/2 w-px h-5 bg-white/10 hidden sm:block"></div>
                <p class="text-[17px] font-bold text-white">930k</p>
                <p class="text-[9px] text-slate-500 font-bold uppercase tracking-widest mt-0.5">CLIP VIEWS</p>
              </div>
              <div class="group cursor-pointer text-center relative flex flex-col items-center">
                <div class="absolute -right-5 top-1/2 -translate-y-1/2 w-px h-5 bg-white/10 hidden sm:block"></div>
                <p class="text-[17px] font-bold text-white">82</p>
                <p class="text-[9px] text-slate-500 font-bold uppercase tracking-widest mt-0.5">CLIPS</p>
              </div>
              <div class="group cursor-pointer text-center relative flex flex-col items-center">
                <div class="absolute -right-5 top-1/2 -translate-y-1/2 w-px h-5 bg-white/10 hidden sm:block"></div>
                <p class="text-[17px] font-bold text-white">5.7K</p>
                <p class="text-[9px] text-slate-500 font-bold uppercase tracking-widest mt-0.5">FOLLOWERS</p>
              </div>
              <div class="group cursor-pointer text-center relative flex flex-col items-center">
                <p class="text-[17px] font-bold text-white">24</p>
                <p class="text-[9px] text-slate-500 font-bold uppercase tracking-widest mt-0.5">FOLLOWING</p>
              </div>
            </div>
            
            <p class="text-[11px] text-slate-400 max-w-[340px] text-center lg:text-right leading-relaxed font-medium">
              Grandmaster Zoe main and always looking for friends to play with. Valorant noobie and I like getting carried ❤️
            </p>
          </div>
        </div>


        <!-- Main Grid (Clips vs Stats) -->
        <div class="grid grid-cols-1 xl:grid-cols-12 gap-8 md:gap-12 mt-6">
          
          <!-- Left Column: Clips -->
          <div class="xl:col-span-8 space-y-6">
            
            <!-- Feed Header -->
            <div class="space-y-4">
              <h2 class="text-xl font-bold text-white tracking-tight">Watching Empre55ive's Latest Clips</h2>
              
              <!-- Tabs -->
              <div class="flex items-center gap-6 border-b border-white/5 pb-0">
                <button 
                  v-for="tab in tabs" 
                  :key="tab"
                  @click="activeTab = tab"
                  class="relative pb-3 text-xs font-bold transition-all"
                  :class="activeTab === tab ? 'text-white' : 'text-slate-500 hover:text-white'"
                >
                  {{ tab }}
                  <div v-if="activeTab === tab" class="absolute bottom-0 left-0 w-full h-[2px] bg-primary shadow-primary/40 rounded-t-full"></div>
                </button>
              </div>

              <!-- Filters -->
              <div class="flex gap-4 pt-2">
                <div>
                  <span class="text-[9px] text-slate-500 font-bold block mb-1 uppercase tracking-widest px-1">Game Filter</span>
                  <button class="bg-surface-container text-white text-[11px] font-medium px-4 py-2.5 rounded-xl flex items-center justify-between min-w-[130px] hover:bg-surface-container-high transition-colors border border-white/5">
                    Valorant <span class="material-symbols-outlined text-[16px] text-slate-400">expand_more</span>
                  </button>
                </div>
                <div>
                  <span class="text-[9px] text-slate-500 font-bold block mb-1 uppercase tracking-widest px-1">Sort by</span>
                  <button class="bg-surface-container text-white text-[11px] font-medium px-4 py-2.5 rounded-xl flex items-center justify-between min-w-[130px] hover:bg-surface-container-high transition-colors border border-white/5">
                    Newest <span class="material-symbols-outlined text-[16px] text-slate-400">expand_more</span>
                  </button>
                </div>
              </div>
            </div>

            <!-- Clip Card -->
            <div class="space-y-6 pt-2">
              <div class="bg-surface-container/80 rounded-[1.5rem] overflow-hidden border border-white/5 flex flex-col">
                <!-- Clip Header -->
                <div class="p-5 flex items-center justify-between">
                  <div class="flex items-center gap-3">
                    <img :src="user.avatar" class="w-8 h-8 rounded-[0.8rem] object-cover" />
                    <h4 class="text-[13px] font-bold text-white">{{ user.name }}</h4>
                  </div>
                  <div class="flex items-center gap-3">
                    <p class="text-[11px] text-slate-400">Zzyzxx is with <strong>Tom Buyea</strong> <span class="bg-white/10 text-white text-[9px] px-2 py-0.5 rounded-md ml-1">+3</span></p>
                    <button class="text-slate-500 hover:text-white transition-colors">
                      <span class="material-symbols-outlined text-lg">more_vert</span>
                    </button>
                  </div>
                </div>

                <!-- Video View -->
                <div class="relative w-full aspect-video bg-black cursor-pointer group">
                  <img src="https://images.contentstack.io/v3/assets/blt7311d63b5823f097/blta2d2ec2f7a950fb0/6036c7e3f8430e104113a29f/Braum_Splash_0.jpg" class="w-full h-full object-cover opacity-90 group-hover:opacity-100 transition-opacity" />
                  <div class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity">
                      <div class="w-14 h-14 bg-black/60 backdrop-blur-md rounded-full flex items-center justify-center border border-white/10">
                         <span class="material-symbols-outlined text-3xl text-white">play_arrow</span>
                      </div>
                  </div>
                </div>

                <!-- Clip Footer area -->
                <div class="p-5">
                   <h3 class="text-base font-bold text-white mb-1">This is a title and it goes here like this, fun</h3>
                   <p class="text-xs text-slate-400">1,459 Views</p>
                   
                   <div class="flex gap-2 mt-4">
                     <span class="text-[10px] text-slate-300 font-medium bg-surface-container-high px-3 py-1.5 rounded-md flex items-center gap-1.5 border border-white/5">
                        <span class="w-2 h-2 rounded-full bg-rose-500"></span> #Valorant
                     </span>
                     <span class="text-[10px] text-slate-300 font-medium bg-surface-container-high px-3 py-1.5 rounded-md flex items-center gap-1.5 border border-white/5">
                        #boomswosh
                     </span>
                     <span class="text-[10px] text-slate-300 font-medium bg-surface-container-high px-3 py-1.5 rounded-md flex items-center gap-1.5 border border-white/5">
                        #duelist
                     </span>
                   </div>
                   
                   <div class="flex gap-3 mt-4">
                      <button class="bg-surface-container-high hover:bg-white/10 transition-colors border border-white/5 rounded-lg px-3 py-1.5 flex items-center gap-2">
                         <span class="w-4 h-4 bg-purple-500 rounded text-[8px] flex items-center justify-center text-white">M</span>
                         <span class="text-[10px] text-slate-300">Little Money - Jumpin Out...</span>
                      </button>
                      <button class="bg-surface-container-high hover:bg-white/10 transition-colors border border-white/5 rounded-lg px-3 py-1.5 flex items-center gap-2">
                         <span class="w-4 h-4 bg-emerald-500 rounded text-[8px] flex items-center justify-center text-white">E</span>
                         <span class="text-[10px] text-slate-300">Emotional Damage</span>
                      </button>
                   </div>
                </div>
              </div>
            </div>
          </div>

          <!-- Right Column: Stats Sidebar -->
          <div class="xl:col-span-4 space-y-6">
            
            <h3 class="text-xs font-bold text-white md:mt-2">Valorant Statistics</h3>

            <!-- Competitive Overview -->
            <div class="bg-surface-container/80 rounded-[1.5rem] p-6 border border-white/5">
               <h4 class="text-[13px] font-bold text-white mb-6">Competitive Overview</h4>
               
               <div class="flex items-center justify-between mt-2">
                  <div class="flex flex-col items-center">
                    <div class="w-[72px] h-[72px] rounded-full border-4 border-primary flex items-center justify-center mb-3 bg-background/50 p-2 relative overflow-hidden">
                       <img :src="competitiveStats.rankIcon" class="w-12 h-12 object-contain" />
                       <div class="absolute inset-0 shadow-[inset_0_0_10px_rgba(var(--color-primary),0.3)] rounded-full"></div>
                    </div>
                    <span class="text-[11px] font-bold text-primary">{{ competitiveStats.rank }}</span>
                  </div>
                  
                  <div class="flex flex-col items-center">
                    <div class="w-[72px] h-[72px] rounded-full border border-white/10 border-t-[#0ea5e9] border-r-[#0ea5e9] border-[3px] flex items-center justify-center mb-3 bg-background/50">
                       <span class="text-[13px] font-bold text-white">{{ competitiveStats.winRate }}</span>
                    </div>
                    <span class="text-[10px] font-semibold text-slate-400">Win Ratio</span>
                  </div>

                  <div class="flex flex-col items-center">
                    <div class="w-[72px] h-[72px] rounded-full border border-white/10 border-t-[#10b981] border-l-[#10b981] border-[3px] flex items-center justify-center mb-3 bg-background/50">
                       <span class="text-[13px] font-bold text-[#10b981]">86W <span class="text-[#f43f5e]">12L</span></span>
                    </div>
                    <span class="text-[10px] font-semibold text-slate-400">Win/Loss</span>
                  </div>
               </div>
            </div>

            <!-- Top Agent Card -->
            <div class="bg-surface-container/80 rounded-[1.5rem] p-6 border border-white/5 relative overflow-hidden">
               <h4 class="text-[13px] font-bold text-white mb-6">Top Agent</h4>
               
               <div class="flex justify-between relative z-10 w-2/3">
                  <div class="flex flex-col">
                    <span class="text-sm font-bold text-white">{{ topChampion.winRate }}</span>
                    <span class="text-[10px] font-medium text-slate-400 mt-1">Win Ratio</span>
                  </div>
                  <div class="flex flex-col">
                    <span class="text-sm font-bold text-white">{{ topChampion.kdRatio }}</span>
                    <span class="text-[10px] font-medium text-slate-400 mt-1">K/D Ratio</span>
                  </div>
                  <div class="flex flex-col">
                    <span class="text-sm font-bold text-white">{{ topChampion.avgDmg }}</span>
                    <span class="text-[10px] font-medium text-slate-400 mt-1">Dmg/Round</span>
                  </div>
               </div>
               
               <img :src="topChampion.image" class="absolute right-0 bottom-0 h-32 object-contain" />
               <h5 class="absolute font-bold text-white text-base right-6 bottom-4 drop-shadow-[0_2px_4px_black]">{{ topChampion.name }}</h5>
            </div>

            <!-- Leaderboard -->
            <div class="bg-surface-container/80 rounded-[1.5rem] p-6 border border-white/5">
               <div class="flex items-center justify-between mb-4">
                  <h4 class="text-[13px] font-bold text-white">Leaderboard</h4>
                  <button class="bg-surface-container-high text-white text-[10px] font-medium px-3 py-1.5 rounded-lg flex items-center justify-between hover:bg-surface-container-highest transition-colors border border-white/5">
                    Valorant <span class="material-symbols-outlined text-[14px] text-slate-400 ml-1">expand_more</span>
                  </button>
               </div>

               <div class="flex items-center gap-2 mb-4 overflow-x-auto no-scrollbar">
                  <button class="bg-background text-slate-300 text-[10px] font-medium px-3 py-1.5 rounded-lg flex items-center hover:text-white transition-colors border border-white/5 whitespace-nowrap">
                    You vs. Friends <span class="material-symbols-outlined text-[14px] text-slate-400 ml-1">expand_more</span>
                  </button>
                  <button class="bg-background text-slate-300 text-[10px] font-medium px-3 py-1.5 rounded-lg flex items-center hover:text-white transition-colors border border-white/5 whitespace-nowrap">
                    NA <span class="material-symbols-outlined text-[14px] text-slate-400 ml-1">expand_more</span>
                  </button>
                  <button class="bg-background text-slate-300 text-[10px] font-medium px-3 py-1.5 rounded-lg flex items-center hover:text-white transition-colors border border-white/5 whitespace-nowrap">
                    Diamond <span class="material-symbols-outlined text-[14px] text-slate-400 ml-1">expand_more</span>
                  </button>
               </div>

               <table class="w-full text-left mt-2 border-collapse">
                 <thead>
                   <tr class="text-[10px] text-slate-500 border-b border-white/5">
                     <th class="py-3 font-medium font-normal w-8 text-center">No.</th>
                     <th class="py-3 font-medium font-normal">Medal User</th>
                     <th class="py-3 font-medium font-normal text-right">Rank</th>
                     <th class="py-3 font-medium font-normal text-right">Followers</th>
                   </tr>
                 </thead>
                 <tbody>
                   <tr v-for="item in leaderboard" :key="item.name" class="border-b border-white/5 last:border-0 hover:bg-white/[0.02] transition-colors cursor-pointer">
                     <td class="py-3 text-[11px] text-slate-400 font-medium text-center">{{ item.rank }}</td>
                     <td class="py-3 flex items-center gap-3">
                        <img :src="item.avatar" class="w-5 h-5 rounded-md object-cover" />
                        <span class="text-[12px] font-medium text-white">{{ item.name }}</span>
                     </td>
                     <td class="py-3 text-right">
                       <!-- empty in the mockup -->
                     </td>
                     <td class="py-3 text-right text-[11px] font-medium text-white">{{ item.points }}</td>
                   </tr>
                 </tbody>
               </table>
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
.no-scrollbar::-webkit-scrollbar {
  display: none;
}
.no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
textarea {
  min-height: 20px;
}
</style>
