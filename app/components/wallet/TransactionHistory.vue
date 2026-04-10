<script setup lang="ts">
interface Transaction {
  id: number
  title: string
  date: string
  amount: string
  status: string
  icon: string
  type: 'incoming' | 'outgoing'
}

const transactions: Transaction[] = [
  {
    id: 1,
    title: 'Tournament Reward: Apex Legends Open',
    date: 'May 14, 2024 • 14:22',
    amount: '+$1,200.00',
    status: 'Completed',
    icon: 'sports_esports',
    type: 'incoming'
  },
  {
    id: 2,
    title: 'Marketplace Sale: Cyber Katana #402',
    date: 'May 12, 2024 • 09:15',
    amount: '+$450.00',
    status: 'Completed',
    icon: 'shopping_cart',
    type: 'incoming'
  },
  {
    id: 3,
    title: 'Withdrawal to Bank Account',
    date: 'May 10, 2024 • 18:40',
    amount: '-$2,000.00',
    status: 'Processing',
    icon: 'payments',
    type: 'outgoing'
  },
  {
    id: 4,
    title: 'Entry Fee: Warzone Global Series',
    date: 'May 08, 2024 • 11:00',
    amount: '-$50.00',
    status: 'Completed',
    icon: 'stadium',
    type: 'outgoing'
  }
]
</script>

<template>
  <section class="space-y-6">
    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-end gap-4">
      <div>
        <h3 class="text-2xl font-bold font-headline text-on-surface">Recent Transactions</h3>
        <p class="text-slate-500 text-sm font-body">Detailed log of your account activity.</p>
      </div>
      <div class="flex gap-3">
        <button class="bg-surface-container-high px-4 py-2 rounded-full text-xs font-bold uppercase tracking-widest text-on-surface-variant hover:bg-surface-variant transition-colors border border-outline-variant/10">Filters</button>
        <button class="bg-surface-container-high px-4 py-2 rounded-full text-xs font-bold uppercase tracking-widest text-on-surface-variant hover:bg-surface-variant transition-colors border border-outline-variant/10">Export CSV</button>
      </div>
    </div>

    <div class="bg-surface-container-low rounded-xl overflow-hidden border border-outline-variant/10">
      <!-- Transaction List Items -->
      <div class="divide-y divide-outline-variant/10">
        <div v-for="tx in transactions" :key="tx.id" class="flex items-center justify-between p-6 hover:bg-surface-container-high transition-colors group">
          <div class="flex items-center gap-6">
            <div 
              class="w-12 h-12 rounded-full flex items-center justify-center"
              :class="tx.type === 'incoming' ? 'bg-primary/10 text-primary' : (tx.status === 'Processing' ? 'bg-error/10 text-error' : 'bg-surface-container-highest text-on-surface-variant')"
            >
              <span class="material-symbols-outlined">{{ tx.icon }}</span>
            </div>
            <div>
              <h4 class="font-bold text-on-surface font-headline">{{ tx.title }}</h4>
              <p class="text-xs text-slate-500 font-label uppercase tracking-wider">{{ tx.date }}</p>
            </div>
          </div>
          <div class="text-right">
            <div 
              class="font-bold text-lg font-headline"
              :class="tx.type === 'incoming' ? 'text-primary' : 'text-on-surface'"
            >
              {{ tx.amount }}
            </div>
            <div class="text-[10px] uppercase tracking-widest text-slate-500">{{ tx.status }}</div>
          </div>
        </div>
      </div>
      <button class="w-full p-6 text-center text-xs font-bold uppercase tracking-[0.2em] text-slate-500 hover:text-primary transition-colors border-t border-outline-variant/10">
        View Full Transaction History
      </button>
    </div>
  </section>
</template>
