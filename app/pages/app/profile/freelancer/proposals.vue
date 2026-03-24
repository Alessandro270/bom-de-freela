<script lang="ts" setup>
definePageMeta({ layout: "app" });

const sentProposals = [
  {
    id: 1,
    jobTitle: "Desenvolvimento de plataforma e-commerce com Nuxt 3",
    clientName: "Maria João",
    sentAt: "20/03/2026",
    value: "320,000.00 KZ",
    status: "pendente" as const,
  },
  {
    id: 2,
    jobTitle: "Criação de API REST para aplicação de gestão escolar",
    clientName: "Carlos Mendes",
    sentAt: "18/03/2026",
    value: "250,000.00 KZ",
    status: "aceite" as const,
  },
  {
    id: 3,
    jobTitle: "Integração com sistema de pagamentos Multicaixa Express",
    clientName: "Luísa Ferreira",
    sentAt: "15/03/2026",
    value: "180,000.00 KZ",
    status: "rejeitado" as const,
  },
  {
    id: 4,
    jobTitle: "Dashboard administrativo para controlo de stocks",
    clientName: "Pedro Nzinga",
    sentAt: "10/03/2026",
    value: "400,000.00 KZ",
    status: "pendente" as const,
  },
  {
    id: 5,
    jobTitle: "Migração de sistema legado PHP para Laravel 11",
    clientName: "Ana Baptista",
    sentAt: "05/03/2026",
    value: "500,000.00 KZ",
    status: "aceite" as const,
  },
];
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileFreelancer>
      <div>PAGINA DE PROJETOS DO FREELANCER</div>
      <div class="space-y-2 *:not-last:border-b *:not-last:border-slate-700">
        <AppUiCardSentProposal
          v-for="proposal in sentProposals"
          :key="proposal.id"
          :id="proposal.id"
          :jobTitle="proposal.jobTitle"
          :clientName="proposal.clientName"
          :sentAt="proposal.sentAt"
          :value="proposal.value"
          :status="proposal.status"
        />
      </div>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
