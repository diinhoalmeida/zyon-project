<script setup lang="ts">
import TournamentMainCard from './TournamentMainCard.vue'
import TournamentInfoCard from './TournamentInfoCard.vue'

interface TournamentDetail {
  label: string
  value: string
  color?: string
}

defineProps<{
  tournament: {
    name: string
    series: string
    image: string
    avatars: string[]
    extraParticipants: number
    isLive?: boolean
  }
  reward: {
    value: string
    subtitle: string
    details: TournamentDetail[]
  }
  protocol: {
    title: string
    subtitle: string
  }
}>()
</script>

<template>
  <section class="mb-12">
    <h2 class="text-sm font-headline uppercase tracking-[0.3em] text-primary mb-6">Torneio Inscrito</h2>
    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
      <TournamentMainCard v-bind="tournament" />
      
      <div class="lg:col-span-4 flex flex-col gap-6">
        <TournamentInfoCard 
          type="reward"
          v-bind="reward"
        />
        <TournamentInfoCard 
          type="protocol"
          v-bind="protocol"
          icon="gavel"
        />
      </div>
    </div>
  </section>
</template>
