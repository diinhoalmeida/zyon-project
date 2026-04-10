<script setup lang="ts">
/**
 * Account Recovery Page for Zyon Arena
 * Matches the Register/Login aesthetic: No-scroll, Split layout, Clean card.
 */

definePageMeta({
  layout: false 
})

useHead({
  title: 'Recuperar Senha | Zyon Arena',
  meta: [
    { name: 'description', content: 'Recupere sua senha e volte para a arena competitiva.' }
  ]
})

const email = ref('')
const loading = ref(false)
const isSubmitted = ref(false)

async function onSubmit() {
  if (!email.value) return
  
  loading.value = true
  // Mock API call
  await new Promise(resolve => setTimeout(resolve, 1500))
  loading.value = false
  isSubmitted.value = true
}

const canSubmit = computed(() => {
  return email.value && email.value.includes('@')
})
</script>

<template>
  <div class="h-screen w-full bg-[#0a0a1a] flex overflow-hidden font-body selection:bg-primary selection:text-on-primary">
    
    <!-- Left Side: Branding/Marketing -->
    <div class="hidden lg:flex lg:w-1/2 h-full relative overflow-hidden ring-1 ring-white/10">
      <img 
        src="/games/register_bg.png" 
        alt="Zyon Arena Safety" 
        class="absolute inset-0 w-full h-full object-cover scale-105 opacity-80 brightness-[0.4]"
      />
      <!-- Masks -->
      <div class="absolute inset-0 bg-linear-to-r from-[#0a0a1a] via-[#0a0a1a]/40 to-transparent"></div>
      <div class="absolute inset-0 bg-linear-to-t from-[#0a0a1a] via-transparent to-transparent opacity-60"></div>
      
      <div class="relative z-10 flex flex-col justify-end p-12 xl:p-20 w-full h-full">
        <div class="max-w-xl">
          <div class="text-2xl font-black text-primary headline-font mb-4 tracking-tighter uppercase">Zyon Security</div>
          <h2 class="text-4xl xl:text-6xl font-bold headline-font text-white leading-[1.1] mb-4 tracking-tighter">
            Sua conta <br/>
            está <span class="text-primary italic underline decoration-white/20 underline-offset-8">segura</span>.
          </h2>
          <p class="text-sm xl:text-lg text-slate-300 font-body leading-relaxed mb-8 opacity-80">
            A proteção dos seus dados e premiações é nossa prioridade máxima. Siga as instruções para recuperar seu acesso.
          </p>
        </div>
      </div>
    </div>

    <!-- Right Side: Compact Centered Card -->
    <div class="w-full lg:w-1/2 h-full flex items-center justify-center p-4 xl:p-8 relative bg-[#0a0a1a]">
      <!-- Decor -->
      <div class="absolute top-0 right-0 w-64 h-64 bg-primary/5 blur-[100px] rounded-full"></div>

      <div class="w-full max-w-[420px] xl:max-w-[460px] relative z-10 flex flex-col items-center">
        
        <!-- Logo Card -->
        <div class="mb-4 xl:mb-6 p-0.5 rounded-2xl primary-gradient shadow-xl">
          <div class="bg-[#0a0a1a] p-3 xl:p-4 rounded-[14px]">
            <div class="w-8 h-8 xl:w-9 xl:h-9 flex items-center justify-center">
              <div class="relative w-full h-full">
                <div class="absolute inset-0 border-[3px] border-primary rounded-md rotate-45"></div>
                <div class="absolute inset-1.5 bg-white rounded-[1px]"></div>
              </div>
            </div>
          </div>
        </div>

        <!-- Header -->
        <div class="text-center mb-6 xl:mb-8">
          <h1 class="text-2xl xl:text-3xl font-bold headline-font text-white mb-1 tracking-tight">Recuperar Acesso</h1>
          <p class="text-slate-500 text-[11px] xl:text-xs font-semibold uppercase tracking-widest opacity-60">Enviaremos instruções para o seu e-mail</p>
        </div>

        <!-- Recovery Card -->
        <div class="w-full bg-white/3 border border-white/10 rounded-[28px] p-8 xl:p-12 backdrop-blur-3xl shadow-2xl mb-8 ring-1 ring-white/5 min-h-[340px] flex flex-col justify-center">
          
          <Transition name="fade" mode="out-in">
            <!-- Form State -->
            <div v-if="!isSubmitted" key="form" class="space-y-8">
              <div class="space-y-3">
                <label class="text-slate-300 font-bold text-[10px] uppercase tracking-[0.2em] ml-1 block">Insira seu E-mail</label>
                <UInput 
                  v-model="email" 
                  type="email" 
                  placeholder="seu@email.com" 
                  size="xl"
                  :ui="{ 
                    base: 'bg-[#0a0a1a]/60 border-slate-800 focus:border-primary transition-all text-white placeholder-slate-700 font-medium',
                    padding: { xl: 'px-6 py-4' },
                    rounded: 'rounded-xl'
                  }"
                />
              </div>

              <UButton 
                size="xl" 
                block 
                class="primary-gradient text-on-primary font-black shadow-xl shadow-primary/20 h-14 rounded-xl text-xs xl:text-sm tracking-widest hover:brightness-110 active:scale-95 transition-all outline-none"
                :loading="loading"
                :disabled="!canSubmit"
                @click="onSubmit"
              >
                ENVIAR INSTRUÇÕES
              </UButton>
            </div>

            <!-- Success State -->
            <div v-else key="success" class="text-center space-y-6">
              <div class="w-16 h-16 bg-primary/10 border border-primary/20 rounded-full flex items-center justify-center mx-auto mb-6">
                <span class="material-symbols-outlined text-primary text-3xl">check_circle</span>
              </div>
              <div>
                <h3 class="text-xl font-bold text-white mb-2 underline decoration-primary decoration-2 underline-offset-4">E-mail Enviado!</h3>
                <p class="text-slate-400 text-sm leading-relaxed">
                  Verifique sua caixa de entrada. Enviamos um link de recuperação para <span class="text-white font-bold">{{ email }}</span>.
                </p>
              </div>
              <UButton 
                variant="ghost" 
                color="gray" 
                class="text-[10px] uppercase tracking-widest hover:text-white"
                @click="isSubmitted = false"
              >
                Não recebeu? Tentar novamente
              </UButton>
            </div>
          </Transition>
        </div>

        <!-- Footer -->
        <div class="text-center text-[10px] xl:text-xs">
          <NuxtLink to="/login" class="flex items-center justify-center gap-2 text-slate-500 hover:text-primary transition-colors font-bold uppercase tracking-[0.2em]">
            <span class="material-symbols-outlined text-sm">arrow_back</span>
            Voltar para o Login
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.primary-gradient {
  background: linear-gradient(135deg, #6366f1 0%, #a855f7 100%);
}

.headline-font {
  font-family: 'Space Grotesk', sans-serif;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
</style>
