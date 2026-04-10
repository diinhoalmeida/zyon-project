<script setup lang="ts">
const route = useRoute()

useHead({
  title: 'Zyon | Sua Carteira',
  bodyAttrs: {
    class: 'bg-[#10102e] text-[#e2dfff] font-["Space_Grotesk"]'
  }
})

const balanceData = {
  active: '4.250',
  pending: '850',
  totalEarnings: '12.420',
  withdrawals: '8.170'
}

const historyFilters = ['Todos', 'Aprovado', 'Pendente', 'Em Revisão']
const activeFilter = ref('Todos')

const transactions = [
  { id: 1, title: 'Saque via Pix', date: '26 Fev', amount: '-1.200', status: 'Aprovado', statusColor: 'text-emerald-400', icon: 'payments' },
  { id: 2, title: 'Inscrição Torneio Blitz', date: '24 Fev', amount: '-50', status: 'Aprovado', statusColor: 'text-emerald-400', icon: 'sports_esports' },
  { id: 3, title: 'Prêmio: Pro League S2', date: '22 Fev', amount: '+2.500', status: 'Aprovado', statusColor: 'text-emerald-400', icon: 'emoji_events' },
  { id: 4, title: 'Bônus de Indicação', date: '20 Fev', amount: '+100', status: 'Pendente', statusColor: 'text-amber-400', icon: 'redeem' },
  { id: 5, title: 'Reembolso: Arena Bug', date: '18 Fev', amount: '+25', status: 'Em Revisão', statusColor: 'text-blue-400', icon: 'history' },
]
</script>

<template>
  <div class="dark min-h-screen bg-[#10102e] text-[#e2dfff] font-['Inter']">
    <AdminSidebar />
    <AdminHeader />

    <main class="min-h-screen transition-[padding] duration-300 lg:pl-[280px] pt-[72px]">
      
      <!-- Centered Container with Responsive Grid -->
      <div class="max-w-[1400px] mx-auto px-4 sm:px-6 lg:px-8 py-8 flex flex-col lg:flex-row gap-8 xl:gap-12">
        
        <!-- Left Column: Balance & Stats (Full width mobile, ~400px desktop) -->
        <div class="w-full lg:w-[380px] xl:w-[420px] shrink-0 space-y-6">
          
          <!-- Header Nav (Mobile Only or Breadcrumb style) -->
          <div class="flex items-center justify-between lg:hidden mb-2">
            <NuxtLink to="/home" class="p-2 -ml-2 rounded-full hover:bg-white/5 transition-colors">
              <span class="material-symbols-outlined text-slate-400">arrow_back</span>
            </NuxtLink>
            <h1 class="text-sm font-bold uppercase tracking-[0.2em] text-white">Sua Carteira</h1>
            <div class="w-10"></div>
          </div>

          <h1 class="hidden lg:block text-2xl font-black text-white uppercase tracking-wider mb-8 font-headline">Sua Carteira</h1>

          <!-- Hero Balance Card -->
          <section class="relative overflow-hidden rounded-[2.5rem] bg-linear-to-br from-primary to-[#2c1370] p-8 shadow-2xl border border-white/10 group min-h-[220px] flex flex-col justify-center">
            <!-- Teemo Background Image -->
            <div class="absolute right-[-5%] bottom-[-5%] w-[60%] lg:w-[70%] pointer-events-none transform group-hover:scale-105 transition-transform duration-700 opacity-90">
               <img src="https://static.wikia.nocookie.net/leagueoflegends/images/1/1d/Teemo_OriginalCentered.jpg/revision/latest/scale-to-width-down/1000?cb=20180414203649" class="w-full object-contain" style="-webkit-mask-image: linear-gradient(to right, transparent 0%, black 50%); mask-image: linear-gradient(to right, transparent 0%, black 50%);" />
            </div>

            <div class="relative z-10">
              <p class="text-[10px] text-white/70 font-bold uppercase tracking-widest mb-1">Saldo Disponível</p>
              <div class="flex items-center gap-2 mb-8">
                <span class="text-4xl xl:text-5xl font-black text-white leading-none">{{ balanceData.active }}</span>
                <span class="text-xs font-bold text-white/50 self-end mb-1 tracking-widest uppercase">ZYN</span>
              </div>
              
              <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-black/20 backdrop-blur-md border border-white/5">
                <span class="material-symbols-outlined text-[14px] text-amber-400 animate-pulse">history</span>
                <span class="text-[10px] text-white font-bold uppercase tracking-wider">Pendente: <span class="text-amber-400">{{ balanceData.pending }} ZYN</span></span>
              </div>
            </div>
          </section>

          <!-- Stats Grid inside Left Col -->
          <div class="grid grid-cols-2 lg:grid-cols-1 gap-4">
            <div class="bg-surface-container/50 rounded-[2rem] p-6 border border-white/5 border-l-4 border-l-emerald-400/50">
              <div class="flex items-center gap-3 mb-2">
                <div class="w-8 h-8 rounded-lg bg-emerald-400/10 flex items-center justify-center">
                  <span class="material-symbols-outlined text-sm text-emerald-400">trending_up</span>
                </div>
                <span class="text-[10px] text-slate-400 font-bold uppercase tracking-wider">Ganhos Totais</span>
              </div>
              <p class="text-2xl font-black text-white leading-tight">{{ balanceData.totalEarnings }} <span class="text-[10px] text-slate-500 font-bold uppercase">ZYN</span></p>
            </div>
            
            <div class="bg-surface-container/50 rounded-[2rem] p-6 border border-white/5 border-l-4 border-l-primary/50">
              <div class="flex items-center gap-3 mb-2">
                <div class="w-8 h-8 rounded-lg bg-primary/10 flex items-center justify-center">
                  <span class="material-symbols-outlined text-sm text-primary">logout</span>
                </div>
                <span class="text-[10px] text-slate-400 font-bold uppercase tracking-wider">Saques Realizados</span>
              </div>
              <p class="text-2xl font-black text-white leading-tight">{{ balanceData.withdrawals }} <span class="text-[10px] text-slate-500 font-bold uppercase">ZYN</span></p>
            </div>
          </div>

          <!-- Desktop Quick CTA -->
          <div class="hidden lg:block p-8 rounded-[2.5rem] bg-linear-to-b from-[#1d1c3a] to-transparent border border-white/5">
            <h3 class="text-white font-bold mb-2 uppercase tracking-widest text-xs">Precisa de Ajuda?</h3>
            <p class="text-slate-400 text-[11px] leading-relaxed mb-6">Seus saques via Pix costumam levar menos de 10 minutos. Caso tenha dúvidas, procure o suporte.</p>
            <button class="w-full py-3 bg-white/5 hover:bg-white/10 text-white text-[10px] font-bold uppercase tracking-widest rounded-xl transition-all border border-white/10">
              Falar com Suporte
            </button>
          </div>
        </div>

        <!-- Right Column: History Section (Expanded) -->
        <section class="flex-1 space-y-6 lg:pt-14">
          <div class="flex items-center justify-between">
            <h2 class="text-sm font-bold uppercase tracking-[0.2em] text-primary">Histórico de Transações</h2>
            <div class="hidden sm:flex items-center gap-2">
              <span class="text-[10px] text-slate-500 font-bold uppercase tracking-widest">Atualizado em tempo real</span>
              <span class="relative flex h-1.5 w-1.5">
                <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span>
                <span class="relative inline-flex rounded-full h-1.5 w-1.5 bg-emerald-500"></span>
              </span>
            </div>
          </div>

          <!-- Filters -->
          <div class="flex gap-2 overflow-x-auto no-scrollbar pb-2">
            <button 
              v-for="filter in historyFilters" 
              :key="filter"
              @click="activeFilter = filter"
              class="px-6 py-3 rounded-xl text-[10px] font-bold uppercase tracking-widest transition-all shrink-0 border"
              :class="activeFilter === filter ? 'bg-primary border-primary text-white shadow-xl shadow-primary/30' : 'bg-surface-container/40 border-white/5 text-slate-400 hover:text-white hover:border-white/10'"
            >
              {{ filter }}
            </button>
          </div>

          <!-- Transaction List -->
          <div class="grid grid-cols-1 gap-3">
            <div 
              v-for="tx in transactions" 
              :key="tx.id"
              class="flex items-center justify-between p-5 rounded-[2rem] bg-surface-container/20 border border-white/5 hover:bg-surface-container/30 hover:border-white/10 transition-all cursor-pointer group"
            >
              <div class="flex items-center gap-5">
                <div class="w-12 h-12 rounded-2xl bg-[#1d1c3a] flex items-center justify-center border border-white/5 group-hover:bg-primary/20 transition-colors shadow-inner">
                  <span class="material-symbols-outlined text-primary text-[22px]">{{ tx.icon }}</span>
                </div>
                <div>
                  <h4 class="text-[14px] font-bold text-white mb-1 group-hover:text-primary transition-colors">{{ tx.title }}</h4>
                  <div class="flex items-center gap-3">
                    <span class="text-[11px] text-slate-500 font-medium">{{ tx.date }}</span>
                    <span class="w-1 h-1 rounded-full bg-slate-700"></span>
                    <span class="text-[10px] font-bold uppercase tracking-tight" :class="tx.statusColor">{{ tx.status }}</span>
                  </div>
                </div>
              </div>
              <div class="text-right">
                <p class="text-lg font-black tracking-wider" :class="tx.amount.startsWith('+') ? 'text-emerald-400' : 'text-white'">
                  {{ tx.amount }}
                </p>
                <p class="text-[10px] text-slate-500 font-bold uppercase tracking-widest">ZYN Tokens</p>
              </div>
            </div>
          </div>
          
          <button class="w-full py-4 border border-dashed border-white/10 rounded-[2rem] text-[10px] font-bold text-slate-500 hover:text-white hover:border-white/20 transition-all uppercase tracking-[0.3em]">
            Carregar Mais Atividade
          </button>
        </section>

      </div>
    </main>

    <AdminFooter />
  </div>
</template>

<style scoped>
.no-scrollbar::-webkit-scrollbar {
  display: none;
}
.no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
</style>

<style scoped>
.glass-effect {
  backdrop-filter: blur(20px);
  background-color: rgba(50, 49, 81, 0.6);
}
</style>
