<script setup lang="ts">
/**
 * Login Page for Zyon Arena
 * Matches the Register page aesthetic: No-scroll, Split layout, Clean card.
 */

definePageMeta({
  layout: false 
})

useHead({
  title: 'Login | Zyon Arena',
  meta: [
    { name: 'description', content: 'Entre na sua conta Zyon e prepare-se para competir.' }
  ]
})

const state = reactive({
  email: '',
  password: '',
  rememberMe: false
})

const loading = ref(false)

async function onSubmit() {
  loading.value = true
  await new Promise(resolve => setTimeout(resolve, 1000))
  loading.value = false
  navigateTo('/game-dashboard')
}

const canSubmit = computed(() => {
  return state.email && state.password
})
</script>

<template>
  <div class="h-screen w-full bg-[#0a0a1a] flex overflow-hidden font-body selection:bg-primary selection:text-on-primary">
    
    <!-- Left Side: Branding/Marketing -->
    <div class="hidden lg:flex lg:w-1/2 h-full relative overflow-hidden ring-1 ring-white/10">
      <img 
        src="/games/register_bg.png" 
        alt="Zyon Arena Login" 
        class="absolute inset-0 w-full h-full object-cover scale-105 opacity-80"
      />
      <!-- Masks -->
      <div class="absolute inset-0 bg-linear-to-r from-[#0a0a1a] via-[#0a0a1a]/40 to-transparent"></div>
      <div class="absolute inset-0 bg-linear-to-t from-[#0a0a1a] via-transparent to-transparent opacity-60"></div>
      
      <div class="relative z-10 flex flex-col justify-end p-12 xl:p-20 w-full h-full">
        <div class="max-w-xl">
          <div class="text-2xl font-black text-primary headline-font mb-4 tracking-tighter uppercase">Zyon Arena</div>
          <h2 class="text-4xl xl:text-6xl font-bold headline-font text-white leading-[1.1] mb-4 tracking-tighter">
            Bom te ver <br/>
            de <span class="text-primary italic underline decoration-white/20 underline-offset-8">volta</span>.
          </h2>
          <p class="text-sm xl:text-lg text-slate-300 font-body leading-relaxed mb-8 opacity-80">
            Sua posição no ranking te espera. Entre agora e continue sua jornada rumo ao topo da elite.
          </p>
          
          <div class="flex gap-8 xl:gap-12">
            <div class="bg-white/5 backdrop-blur-md border border-white/10 p-4 rounded-2xl">
              <div class="text-xl xl:text-2xl font-bold headline-font text-white">Ativo</div>
              <div class="text-[8px] xl:text-[9px] uppercase tracking-[0.2em] text-primary font-bold">Status Arena</div>
            </div>
          </div>
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
          <h1 class="text-2xl xl:text-3xl font-bold headline-font text-white mb-1 tracking-tight">Login na Arena</h1>
          <p class="text-slate-500 text-[11px] xl:text-xs font-semibold uppercase tracking-widest opacity-60">Entre para competir agora</p>
        </div>

        <!-- Login Card -->
        <div class="w-full bg-white/3 border border-white/10 rounded-[28px] p-6 xl:p-10 backdrop-blur-3xl shadow-2xl mb-6 ring-1 ring-white/5">
          <UForm :state="state" class="space-y-6 xl:space-y-8" @submit="onSubmit">
            
            <div class="space-y-2">
              <label class="text-slate-400 font-bold text-[9px] xl:text-[10px] uppercase tracking-[0.2em] ml-1 block">E-mail de Acesso</label>
              <UInput 
                v-model="state.email" 
                type="email" 
                placeholder="seu@email.com" 
                size="md"
                :ui="{ 
                  base: 'bg-[#0a0a1a]/60 border-slate-800 focus:border-primary transition-all text-white placeholder-slate-700 font-medium',
                  padding: { md: 'px-5 py-3 xl:py-3.5' },
                  rounded: 'rounded-xl'
                }"
              />
            </div>

            <div class="space-y-2">
              <div class="flex justify-between items-center px-1">
                <label class="text-slate-400 font-bold text-[9px] xl:text-[10px] uppercase tracking-[0.2em] block">Sua Senha</label>
                <NuxtLink to="/forgot-password" class="text-[9px] xl:text-[10px] text-primary hover:underline font-bold uppercase tracking-wider">Esqueceu?</NuxtLink>
              </div>
              <UInput 
                v-model="state.password" 
                type="password" 
                placeholder="••••••••" 
                size="md"
                :ui="{ 
                  base: 'bg-[#0a0a1a]/60 border-slate-800 focus:border-primary transition-all text-white placeholder-slate-700 font-medium',
                  padding: { md: 'px-5 py-3 xl:py-3.5' },
                  rounded: 'rounded-xl'
                }"
              />
            </div>

            <div class="flex items-center gap-2 py-1">
              <UCheckbox v-model="state.rememberMe" name="remember" size="sm" />
              <label class="text-[9px] xl:text-[10px] text-slate-500 font-medium cursor-pointer">
                Manter conectado nesta sessão.
              </label>
            </div>

            <UButton 
              type="submit" 
              size="xl" 
              block 
              class="primary-gradient text-on-primary font-black shadow-xl shadow-primary/20 h-11 xl:h-13 rounded-xl text-xs xl:text-sm tracking-widest hover:brightness-110 active:scale-95 transition-all outline-none"
              :loading="loading"
              :disabled="!canSubmit"
            >
              ENTRAR NA CONTA
            </UButton>
          </UForm>
        </div>

        <!-- Divider -->
        <div class="w-full flex items-center mb-6 px-8">
          <div class="flex-grow h-px bg-white/5"></div>
          <span class="px-3 text-[9px] text-slate-600 font-bold uppercase tracking-[0.3em]">ou continue com</span>
          <div class="flex-grow h-px bg-white/5"></div>
        </div>

        <!-- Social Buttons -->
        <div class="w-full grid grid-cols-2 gap-3 mb-8 px-6">
          <button class="flex items-center justify-center gap-2.5 bg-white/5 border border-white/10 py-2.5 xl:py-3 rounded-xl hover:bg-white/10 transition-colors group">
            <img src="https://www.google.com/favicon.ico" class="w-3.5 h-3.5 grayscale opacity-40 group-hover:opacity-100 group-hover:grayscale-0 transition-all" />
            <span class="text-[9px] font-bold text-slate-400 uppercase tracking-widest">Google</span>
          </button>
          <button class="flex items-center justify-center gap-2.5 bg-white/5 border border-white/10 py-2.5 xl:py-3 rounded-xl hover:bg-white/10 transition-colors group">
            <img src="https://discord.com/favicon.ico" class="w-3.5 h-3.5 grayscale opacity-40 group-hover:opacity-100 group-hover:grayscale-0 transition-all" />
            <span class="text-[9px] font-bold text-slate-400 uppercase tracking-widest">Discord</span>
          </button>
        </div>

        <!-- Footer -->
        <div class="text-center text-[10px] xl:text-xs">
          <span class="text-slate-500 font-medium tracking-wide">Ainda não faz parte?</span>
          <NuxtLink to="/register" class="text-primary font-bold ml-1.5 hover:underline uppercase tracking-widest">Criar Conta</NuxtLink>
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
</style>
