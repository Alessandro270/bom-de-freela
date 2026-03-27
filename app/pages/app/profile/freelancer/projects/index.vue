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
      <!-- Cabeçalho da secção -->
      <div class="flex items-center justify-between mb-4">
        <div class="flex items-center gap-2">
          <h2
            class="text-sm font-semibold text-gray-700 dark:text-gray-300 uppercase tracking-wide"
          >
            Projetos
          </h2>
          <UBadge color="neutral" variant="subtle" size="xs">
            {{ projects.length }}
          </UBadge>
        </div>
      </div>

      <!-- Lista de projetos -->
      <div class="divide-y divide-gray-100 dark:divide-gray-800">
        <AppUiCardProject
          v-for="project in projects"
          :key="project.id"
          :id="project.id"
          :title="project.title"
          :accepted-at="project.acceptedAt"
          :deadline="project.deadline"
          :client-name="project.clientName"
          :status="project.status"
          :to="`/app/profile/freelancer/projects/${project.id}`"
        />
      </div>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
