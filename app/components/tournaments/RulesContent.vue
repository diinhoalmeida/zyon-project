<script setup lang="ts">
/**
 * RulesContent Component
 * Displays formatted rules within the Tournament Details page.
 */
</script>

<template>
  <div class="bg-surface-container-low border border-outline-variant/10 rounded-2xl p-6 sm:p-10 shadow-2xl backdrop-blur-sm prose prose-invert max-w-none prose-headings:font-headline prose-p:text-slate-300 prose-li:text-slate-300">
    <div class="flex items-center gap-3 mb-8 pb-6 border-b border-outline-variant/10">
      <div class="w-12 h-12 bg-primary/10 rounded-xl flex items-center justify-center border border-primary/20">
        <span class="material-symbols-outlined text-primary text-2xl">gavel</span>
      </div>
      <div>
        <h2 class="text-2xl font-headline font-bold text-white m-0">Regras Oficiais do Torneio</h2>
        <p class="text-xs text-primary tracking-[0.2em] uppercase font-bold m-0 mt-1">Leia com atenção antes de competir</p>
      </div>
    </div>

    <div class="grid grid-cols-1 lg:grid-cols-2 gap-x-12 gap-y-8">
      <!-- Section 1 -->
      <div>
        <h3 class="flex items-center gap-2 text-lg text-white mb-4">
          <span class="material-symbols-outlined text-sm text-primary">schedule</span>
          1. Formato e Horários
        </h3>
        <ul class="space-y-2 marker:text-primary">
          <li><strong>Check-in:</strong> Todos os jogadores devem realizar o check-in 15 minutos antes do início do torneio.</li>
          <li><strong>Atrasos:</strong> Haverá uma tolerância máxima de 5 minutos. Após isso, será declarado W.O.</li>
          <li><strong>Tempo de Partida:</strong> O torneio será executado no formato pré-estabelecido (ex: Melhor de 3). Certifique-se de iniciar as partidas dentro do período ativo.</li>
        </ul>
      </div>

      <!-- Section 2 -->
      <div>
        <h3 class="flex items-center gap-2 text-lg text-white mb-4">
          <span class="material-symbols-outlined text-sm text-secondary">monitor</span>
          2. Conexão e Desconexões
        </h3>
        <ul class="space-y-2 marker:text-secondary">
          <li>É responsabilidade do jogador manter uma conexão estável.</li>
          <li><strong>Queda na sala de espera:</strong> Remake permitido.</li>
          <li><strong>Queda durante a partida (após o start):</strong> A partida continua. Se o jogador não conseguir reconectar, a vitória será concedida ao oponente ou registrada de acordo com o progresso atual.</li>
        </ul>
      </div>

      <!-- Section 3 -->
      <div>
        <h3 class="flex items-center gap-2 text-lg text-white mb-4">
          <span class="material-symbols-outlined text-sm text-yellow-500">sports_esports</span>
          3. Fair Play e Conduta
        </h3>
        <ul class="space-y-2 marker:text-yellow-500">
          <li>Uso de cheats, macros não permitidos, ou qualquer software de terceiros que dê vantagem é <strong>estritamente proibido</strong> e resultará em banimento permanente da plataforma.</li>
          <li>Comportamento tóxico no chat (ofensas, racismo, etc) resultará em desclassificação imediata.</li>
          <li>A decisão da administração Zyon é final e inquestionável.</li>
        </ul>
      </div>

      <!-- Section 4 -->
      <div>
        <h3 class="flex items-center gap-2 text-lg text-white mb-4">
          <span class="material-symbols-outlined text-sm text-primary">monetization_on</span>
          4. Distribuição de Prêmios
        </h3>
        <ul class="space-y-2 marker:text-primary">
          <li>A premiação será creditada diretamente na Wallet Zyon em até 48 horas úteis após o término e auditoria do torneio.</li>
          <li>Em caso de empate na fase de grupos, os critérios de desempate serão: 1) Confronto direto, 2) Saldo de vitórias/pontos, 3) Tempo de jogo.</li>
        </ul>
      </div>
    </div>
    
    <div class="mt-8 pt-6 border-t border-outline-variant/10 text-center">
      <p class="text-xs text-slate-500 font-medium">
        Ao clicar em "Entrar", você concorda automaticamente com todos os termos e regras estabelecidos acima.
      </p>
    </div>
  </div>
</template>

<style scoped>
.font-headline {
  font-family: 'Space Grotesk', sans-serif;
}
</style>
