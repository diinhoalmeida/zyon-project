<template>
  <section class="py-24 bg-surface-container-low px-8">
    <div class="container mx-auto max-w-screen-2xl">
      <div class="flex justify-between items-end mb-16">
        <div>
          <h2 class="text-4xl md:text-5xl headline-font font-bold">Arenas em Destaque</h2>
          <p class="text-slate-500 mt-2">Descubra os títulos com as maiores premiações da semana.</p>
        </div>
        <button class="text-primary headline-font uppercase text-sm tracking-[0.15em] flex items-center gap-2 hover:gap-4 transition-all group">
          Ver Tudo 
          <span class="material-symbols-outlined transition-transform group-hover:translate-x-1">trending_flat</span>
        </button>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-12 gap-8 h-auto md:h-[600px]">
        <!-- Main Card -->
        <div class="md:col-span-7 group relative rounded-2xl overflow-hidden bg-surface-container shadow-xl min-h-[400px]">
          <img 
            alt="Cyberpunk Game" 
            class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110" 
            src="https://lh3.googleusercontent.com/aida-public/AB6AXuADy2GCzkq_TwjkFwKWsXkseQYWYcys5oPhKEayOmAslaB_1eGPCufAmuSJaNIZxSSrxOKGOBJIs6CxV_XWVUiMP-mSf21kWhhauLRwR3e480jptqZGE-3w3DMAFQUswE0lSMoTACsb1a3Ni18l8ThZDAzx8TymrIZfYLzfp74TuLovp8fQwlSD7xHBvPcrofUYH7TQGLaIFl79YytDMFSsng8QpkIN4t1p07FlCmEUmMKtxMvU3kUF44NVWycQ-8SJk5LT-8yvE68"
          />
          <div class="absolute inset-0 bg-gradient-to-t from-surface-container-lowest via-transparent to-transparent"></div>
          <div class="absolute top-6 right-6">
            <span class="bg-primary/90 text-on-primary px-4 py-2 rounded-lg headline-font font-bold text-sm shadow-xl backdrop-blur-md">
              Premiação: $25.000
            </span>
          </div>
          <div class="absolute bottom-0 left-0 p-8">
            <span class="text-[10px] font-bold bg-primary-container text-on-primary-container px-3 py-1 rounded-full mb-4 inline-block headline-font">FPS • TÁTICO</span>
            <h3 class="text-3xl font-bold headline-font mb-2">Neon Vanguard</h3>
            <p class="text-slate-400 max-w-md">Domine as ruas de Neo-Tokyo e conquiste sua fatia da premiação em torneios diários.</p>
          </div>
        </div>

        <!-- Side Grid -->
        <div class="md:col-span-5 grid grid-rows-2 gap-8">
          <div class="group relative rounded-2xl overflow-hidden bg-surface-container min-h-[250px]">
            <img 
              alt="Fantasy Game" 
              class="w-full h-full object-cover opacity-80 group-hover:opacity-100 transition-all" 
              src="https://lh3.googleusercontent.com/aida-public/AB6AXuCP98JA4XwnKeY7h2j-yOa8TNX8I98ol6Oocg_baONAxFRhcOeETHgh1jV8onGeckGyw-mKP0smzPdTrz9L6gUVMHvAYgSSHri_ZHFe6Qytf9wmMgHQ2LEsvQDWSCPohKWHAySUv5jnT2mEmDP_GkWxZdkmaUtaRHY2cqCRpPqgcZlhm6mvyqEduxOGYgxAOOWH86_YUTGwQJWnLonLBggUwBWEtF1am9L7ND6n-w1ing0a8pwQY2Jx40z9Ogca4WH8FbzntEAlnj8"
            />
            <div class="absolute inset-0 glass-panel opacity-0 group-hover:opacity-100 transition-opacity flex items-center justify-center">
              <button class="primary-gradient p-4 rounded-full shadow-lg">
                <span class="material-symbols-outlined text-on-primary">play_arrow</span>
              </button>
            </div>
            <div class="absolute top-4 right-4 animate-bounce">
              <span class="bg-secondary/90 text-on-secondary px-3 py-1 rounded text-[10px] font-bold headline-font">
                POOL: $5.000
              </span>
            </div>
            <div class="absolute bottom-6 left-6">
              <h4 class="text-xl font-bold headline-font">Ethereal Skies</h4>
            </div>
          </div>
 
          <div class="group relative rounded-2xl overflow-hidden bg-surface-container min-h-[250px]">
            <img 
              alt="Sci-Fi Game" 
              class="w-full h-full object-cover opacity-80 group-hover:opacity-100 transition-all" 
              src="https://lh3.googleusercontent.com/aida-public/AB6AXuDNjy-ZVFXx0O4UojruKjsJfBeWJzoDl_GGGsrKBwUhDBGYgJafFmRTwwTW-rOuWxHMAoyt09m6Ez4-uYqRllRtfrFAX6qAUBeucGr-m0R3_7wPGe0CIWHqcJP4qIyiURXCr2M_Jsyy4ry_qm1U2gSp_aQJ5QVc2RJmKNnEnEkTZg5D5E7nWSHOTHcYRkM_AppGCEA5WZ4e0_0YIGWus9hljGdgcsvu-EZBpCG9_wTk1JenXvwr_57y4_6QcPpWplfAE5S6n-Oc9S8"
            />
            <div class="absolute inset-0 glass-panel opacity-0 group-hover:opacity-100 transition-opacity flex items-center justify-center">
              <button class="primary-gradient p-4 rounded-full shadow-lg">
                <span class="material-symbols-outlined text-on-primary">play_arrow</span>
              </button>
            </div>
            <div class="absolute top-4 right-4">
              <span class="bg-tertiary/90 text-on-tertiary px-3 py-1 rounded text-[10px] font-bold headline-font">
                RANKED: ATIVO
              </span>
            </div>
            <div class="absolute bottom-6 left-6">
              <h4 class="text-xl font-bold headline-font">Orion's Reach</h4>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// Featured games logic
</script>
