<script setup lang="ts">
/**
 * EntryConfirmationModal Component
 * Prompts the user to choose their payment method based on their Wallet balances.
 */

defineProps<{
  isOpen: boolean
  tournamentTitle: string
  feeReal: string
  feeZyon: string
  penaltyPercentage: number
}>()

const emit = defineEmits<{
  (e: 'close'): void
  (e: 'confirm', method: 'fiat' | 'zyon'): void
}>()

// Mock Wallet Balances
const walletReal = '$ 45.00'
const walletZyon = '3.500 ZC'

</script>

<template>
  <Transition name="fade">
    <div v-if="isOpen" class="fixed inset-0 z-50 flex items-center justify-center px-4">
      <!-- Backdrop -->
      <div class="absolute inset-0 bg-background/80 backdrop-blur-sm" @click="emit('close')"></div>
      
      <!-- Modal Content -->
      <div class="relative bg-surface-container-low border border-outline-variant/20 rounded-3xl shadow-2xl w-full max-w-lg overflow-hidden flex flex-col max-h-[90vh]">
        
        <!-- Header -->
        <div class="px-6 py-5 border-b border-outline-variant/10 flex items-center justify-between bg-surface-container-highest/30">
          <h3 class="font-headline font-bold text-lg text-white">Confirmar Inscrição</h3>
          <button @click="emit('close')" class="w-8 h-8 flex items-center justify-center rounded-full hover:bg-surface-container-highest text-slate-400 hover:text-white transition-colors outline-none">
            <span class="material-symbols-outlined text-sm">close</span>
          </button>
        </div>

        <div class="p-6 sm:p-8 overflow-y-auto custom-scrollbar">
          
          <div class="mb-6 text-center">
            <p class="text-xs text-slate-400 uppercase tracking-widest font-bold mb-1">Torneio</p>
            <h4 class="text-xl font-headline font-bold text-white tracking-wide">{{ tournamentTitle }}</h4>
          </div>

          <!-- Payer Balances -->
          <div class="bg-surface-container-highest rounded-2xl p-4 mb-6 border border-outline-variant/10 flex justify-between items-center">
            <div class="flex flex-col">
              <span class="text-[10px] text-slate-500 uppercase tracking-widest font-bold mb-0.5">Seu Saldo Total</span>
            </div>
            <div class="flex gap-4">
              <div class="flex flex-col items-end">
                <span class="text-white font-bold text-sm">{{ walletReal }}</span>
                <span class="text-[9px] text-slate-400 uppercase">Dinheiro</span>
              </div>
              <div class="w-px h-8 bg-outline-variant/20"></div>
              <div class="flex flex-col items-end">
                <span class="text-primary font-bold text-sm flex items-center gap-1"><span class="material-symbols-outlined text-[10px]">token</span>{{ walletZyon }}</span>
                <span class="text-[9px] text-slate-400 uppercase">Zyon Coins</span>
              </div>
            </div>
          </div>

          <p class="text-xs text-center text-slate-300 mb-6 px-4">
            Escolha qual saldo você deseja utilizar para pagar a taxa de entrada deste torneio.
          </p>

          <div class="space-y-4">
            <!-- Fiat Option -->
            <button 
              @click="emit('confirm', 'fiat')"
              class="w-full relative overflow-hidden group bg-surface-container hover:bg-surface-container-high border border-outline-variant/20 hover:border-green-500/50 rounded-2xl p-4 text-left transition-all outline-none"
            >
              <div class="flex items-center justify-between relative z-10">
                <div class="flex items-center gap-3">
                  <div class="w-10 h-10 rounded-full bg-green-500/10 flex items-center justify-center border border-green-500/20">
                    <span class="material-symbols-outlined text-green-400" style="font-variation-settings: 'FILL' 1;">attach_money</span>
                  </div>
                  <div>
                    <h5 class="text-white font-bold text-sm mb-0.5">Dinheiro (Wallet)</h5>
                    <p class="text-[10px] text-green-400 uppercase tracking-widest font-bold">100% dos Rendimentos</p>
                  </div>
                </div>
                <div class="text-right">
                  <span class="block text-green-400 font-bold text-lg tabular-nums">{{ feeReal }}</span>
                </div>
              </div>
            </button>

            <!-- Zyon Option -->
            <button 
              @click="emit('confirm', 'zyon')"
              class="w-full relative overflow-hidden group bg-surface-container hover:bg-surface-container-high border border-outline-variant/20 hover:border-primary/50 rounded-2xl p-4 text-left transition-all outline-none"
            >
              <div class="flex items-center justify-between relative z-10">
                <div class="flex flex-col justify-center items-start gap-3">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center border border-primary/20">
                      <span class="material-symbols-outlined text-primary text-xl" style="font-variation-settings: 'FILL' 1;">token</span>
                    </div>
                    <div>
                      <h5 class="text-white font-bold text-sm mb-0.5">Zyon Coins</h5>
                      <p class="text-[10px] text-primary uppercase tracking-widest font-bold flex items-center gap-1">Entrada usando tokens
                      </p>
                    </div>
                  </div>
                  <div class="bg-red-500/10 border border-red-500/20 px-3 py-1.5 rounded-lg">
                    <p class="text-[9px] text-red-400 uppercase tracking-widest font-bold flex items-center gap-1">
                      <span class="material-symbols-outlined text-[12px]">warning</span>
                      Rateio Reduzido em {{ penaltyPercentage }}%
                    </p>
                  </div>
                </div>
                
                <div class="text-right shrink-0">
                  <span class="block text-primary font-bold text-lg tabular-nums">{{ feeZyon }} ZC</span>
                </div>
              </div>
            </button>
          </div>

        </div>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.font-headline {
  font-family: 'Space Grotesk', sans-serif;
}
.custom-scrollbar::-webkit-scrollbar {
  width: 4px;
}
.custom-scrollbar::-webkit-scrollbar-track {
  background: transparent;
}
.custom-scrollbar::-webkit-scrollbar-thumb {
  background: rgba(255,255,255,0.1);
  border-radius: 4px;
}

/* Transitions */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.fade-enter-active .relative,
.fade-leave-active .relative {
  transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}
.fade-enter-from .relative,
.fade-leave-to .relative {
  transform: scale(0.95);
}
</style>
