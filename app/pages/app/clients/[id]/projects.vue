<script lang="ts" setup>
definePageMeta({ layout: "app" });

const projects = [
  {
    id: 1,
    title: "Desenvolvimento de App Mobile E-commerce",
    acceptedAt: "12 Mar 2024",
    deadline: "12 Jun 2024",
    clientName: "Alessandro Almeida",
    status: "em_progresso" as const,
  },
  {
    id: 2,
    title: "Refatoração de Sistema de Gestão Escolar",
    acceptedAt: "05 Jan 2024",
    deadline: "15 Fev 2024",
    clientName: "Alessandro Almeida",
    status: "concluido" as const,
  },
  {
    id: 3,
    title: "Criação de Plataforma de Reservas Online",
    acceptedAt: "10 Nov 2023",
    deadline: "20 Dez 2023",
    clientName: "Alessandro Almeida",
    status: "concluido" as const,
  },
];
</script>

<template>
  <AppLayoutClientPublic>
    <!-- Section Header -->
    <div class="flex items-center gap-2 mb-4">
      <h2
        class="text-sm font-semibold text-gray-700 dark:text-gray-300 uppercase tracking-wide"
      >
        Projetos Publicados
      </h2>
      <UBadge color="neutral" variant="subtle" size="xs">{{
        projects.length
      }}</UBadge>
    </div>

    <!-- Projects List -->
    <ul class="divide-y divide-gray-100 dark:divide-gray-800">
      <AppUiCardProject
        v-for="project in projects"
        :key="project.id"
        :id="project.id"
        :title="project.title"
        :acceptedAt="project.acceptedAt"
        :deadline="project.deadline"
        :clientName="project.clientName"
        :status="project.status"
        :to="`/app/proposals/${project.id}`"
      />
    </ul>
  </AppLayoutClientPublic>
</template>
