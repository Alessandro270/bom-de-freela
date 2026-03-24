<script lang="ts" setup>
definePageMeta({ layout: "app" });
const projects = [
  {
    id: 1,
    title: "Sistema de gestão de pagamentos para e-commerce",
    acceptedAt: "10/03/2026",
    deadline: "30/03/2026",
    clientName: "Maria João",
    status: "em_progresso" as const,
  },
  {
    id: 2,
    title: "Desenvolvimento de API REST para plataforma mobile",
    acceptedAt: "05/02/2026",
    deadline: "28/02/2026",
    clientName: "Carlos Mendes",
    status: "concluido" as const,
  },
  {
    id: 3,
    title: "Criação de dashboard administrativo com Vue 3",
    acceptedAt: "18/03/2026",
    deadline: "10/04/2026",
    clientName: "Luísa Ferreira",
    status: "em_progresso" as const,
  },
  {
    id: 4,
    title: "Integração com gateway de pagamento Multicaixa Express",
    acceptedAt: "01/01/2026",
    deadline: "20/01/2026",
    clientName: "Pedro Nzinga",
    status: "concluido" as const,
  },
];
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileFreelancer>
      <AppUiHeaderProfile class="flex justify-between">
        <span>Projetos</span>
        <span class="text-slate-400"> (4)</span>
      </AppUiHeaderProfile>
      <div class="space-y-2 *:not-last:border-b *:not-last:border-slate-700">
        <AppUiCardProject
          v-for="project in projects"
          :key="project.id"
          :id="project.id"
          :title="project.title"
          :accepted-at="project.acceptedAt"
          :deadline="project.deadline"
          :client-name="project.clientName"
          :status="project.status"
        />
      </div>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
