<script setup lang="ts">
import TournamentHero from '~/components/tournaments/TournamentHero.vue'
import TournamentFilters from '~/components/tournaments/TournamentFilters.vue'
import TournamentTable from '~/components/tournaments/TournamentTable.vue'
import EntryConfirmationModal from '~/components/tournaments/EntryConfirmationModal.vue'

/**
 * Tournament Arena Page
 * Mobile-First Responsive version.
 */

useHead({
  title: 'Arena de Torneios | Zyon',
  bodyAttrs: {
    class: 'bg-background text-on-surface selection:bg-primary selection:text-on-primary'
  }
})

const heroData = {
  title: 'ARENA DE TORNEIOS',
  subtitle: 'Reúna-se. Compita. conquiste.',
  image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBDfRypHrN2loWiVumTzx9j8SRUDs0X28CO85Cf5wIF87B0TWNzYSbAzQhh7sed9c1LzaK3IH5xBRmSq2g7Ed7aV0QuvgapCISlnu9--mSXJl16tpdkpSdQHFXbmGwyKS4LQyw4OVmGCkWcHKD2hJO73_z3kwVWybj7V6GfnqxpTe79v5eZ42eNZB5xi0svpeB8Hz_cdgfBl66Y3cDthqs-xp9sIh7iWGGceDodaU3Ls0IiF1LrM94oW1u6FeGuSq270ebFeWZU3Xs',
  dataAlt: 'Arena futurista de e-sports com luzes de neon brilhantes'
}

const tournaments = [
  {
    id: 'cyber-strike-elite',
    name: 'CYBER STRIKE ELITE',
    game: 'Neon Siege',
    prize: '$12,500',
    participants: 128,
    maxParticipants: 256,
    status: 'Inscrições Abertas',
    statusClass: 'bg-green-500/10 text-green-400 border-green-500/20',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuA0JPYvbLE4Z2o1t-FiXxrjfnY59bKItPDGJYoRhEZN2FcA-dUV6fRJ1cV82VU8Ve7l4gRcbWIbFbMBVo2BcJRPL4CbFUuB_xpUyw8l1rnbscR2psjx9WDX0m5tm4UBy1Dwwd6oHFygW6ru8yhzeu9OPLzVKONiW3koHe1xabA5Z2Ce5OgwVjwlGRocji6AAqKs3GOL-VBMg--OJeNuzzVqEHSuVhECPmqedFxVO--j_PCHWCT_I6a593GM1h420nZ2vGCuPvA1PqY',
    canJoin: true,
    progress: 50,
    type: 'best_of_3',
    typeName: 'Melhor de 3',
    startTime: '2024-04-10T14:00:00Z',
    endTime: '2024-04-10T20:00:00Z',
    matchesPlayed: 1,
    totalMatchesNeeded: 3,
    feeReal: '$ 15.00',
    feeZyon: '1.500 ZC'
  },
  {
    id: 'galaxy-drift-pro',
    name: 'GALAXY DRIFT PRO',
    game: 'Hyperdrift Ultra',
    prize: '$5,000',
    participants: 64,
    maxParticipants: 64,
    status: 'Lotado',
    statusClass: 'bg-secondary/10 text-secondary border-secondary/20',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuDUDmPm0vgjwUKIAbqcfoE5Nh6bLSTE8IYyFEGceLaqWt8hznEn8TOkhjOWQYjQxPppb5bFpnAVTzrSilaexmiXr9kg2u9zpEsfEG29B0_zByNyEJD9G63cLjWN-8KGsVvIm_OvNfxR2pNqDm6pgk61KnJ7O2_KioHNg-2JdhhqMZsFbA27qS-FERY81ZuGROgzM3MuaWKBB2k0p92Jor4YsPf2hR0wdv2LUtfnC3bpbIGapHnQp3d-eFetFH3M1L_N_rdXcX_ciMc',
    canJoin: false,
    progress: 100,
    type: 'best_of_5',
    typeName: 'Melhor de 5',
    startTime: '2024-04-11T16:00:00Z',
    endTime: '2024-04-11T22:00:00Z',
    matchesPlayed: 0,
    totalMatchesNeeded: 5,
    feeReal: '$ 5.00',
    feeZyon: '500 ZC'
  },
  {
    id: 'void-masters-iv',
    name: 'VOID MASTERS IV',
    game: 'Void Runner',
    prize: '$2,500',
    participants: 12,
    maxParticipants: 32,
    status: 'Inscrições Abertas',
    statusClass: 'bg-green-500/10 text-green-400 border-green-500/20',
    image: 'https://lh3.googleusercontent.com/aida-public/AB6AXuDL568naZn6JsfBaiAQeNGpu8POfCLdw7wY2d9lA5g_tQ-2KwU-uiHT2aTp9iJF0fo775ypO6Y5HUDrfxcN4CnxnYzZf-hm8ijtgx8yJS98MN5MedK4oTJWCnaCaE7nXSAxiCKMnA98k_b-6MtQ45ta-uL8y3ydDgGuxW3rzSuypEzEneaw5YVpxlOsiptUxd_aZ60at0jbVzbvduDI5Dz5KTAu1Cqj3cy9psk44n4UBVeB8JRHlqXdSQyY9UQoOOeKF-6mz23YDh0',
    canJoin: true,
    progress: 33,
    type: 'play_2',
    typeName: 'Jogue 2',
    startTime: '2024-04-09T18:00:00Z',
    endTime: '2024-04-09T21:00:00Z',
    matchesPlayed: 2,
    totalMatchesNeeded: 2,
    feeReal: '$ 2.00',
    feeZyon: '200 ZC'
  }
]

const isModalOpen = ref(false)
const selectedTournament = ref<any>(null)

const openJoinModal = (tournament: any) => {
  selectedTournament.value = tournament
  isModalOpen.value = true
}

const handleEntryConfirm = (method: 'fiat' | 'zyon') => {
  console.log('Joined from Arena via method:', method)
  isModalOpen.value = false
}
</script>

<template>
  <div class="dark min-h-screen bg-background text-on-surface">
    <AdminSidebar />

    <main class="min-h-screen transition-[padding] duration-300 lg:pl-[280px]">
      <AdminHeader />

      <div class="pt-20 lg:pt-24 px-4 sm:px-10 lg:px-12 pb-12 max-w-screen-2xl mx-auto space-y-2 sm:space-y-4">
        
        <TournamentHero v-bind="heroData" />

        <div class="space-y-6 sm:space-y-10">
          <TournamentFilters />
          <TournamentTable 
            :tournaments="tournaments" 
            @join="openJoinModal"
          />
        </div>

        <AdminFooter />

        <!-- Payment Modal from Arena -->
        <EntryConfirmationModal 
          v-if="selectedTournament"
          :is-open="isModalOpen"
          :tournament-title="selectedTournament.name"
          :fee-real="selectedTournament.feeReal"
          :fee-zyon="selectedTournament.feeZyon"
          :penalty-percentage="30"
          @close="isModalOpen = false"
          @confirm="handleEntryConfirm"
        />
      </div>
    </main>
  </div>
</template>
