<script lang="ts" setup>
definePageMeta({ layout: "app" });

const projects = [
  {
    id: 1,
    title: "Desenvolvimento de plataforma e-commerce com Nuxt 3",
    freelancerName: "Marcos Silva",
    acceptedAt: "10/03/2026",
    deadline: "30/03/2026",
    status: "em_progresso" as const,
  },
  {
    id: 2,
    title: "Criação de API REST para aplicação de gestão escolar",
    freelancerName: "Ana Ferreira",
    acceptedAt: "05/02/2026",
    deadline: "28/02/2026",
    status: "concluido" as const,
  },
  {
    id: 3,
    title: "Dashboard administrativo para controlo de stocks",
    freelancerName: "João Baptista",
    acceptedAt: "18/03/2026",
    deadline: "15/04/2026",
    status: "em_progresso" as const,
  },
];
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileClient>
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
        <div
          v-for="project in projects"
          :key="project.id"
          class="py-4 flex items-start justify-between gap-6"
        >
          <!-- Info -->
          <div class="space-y-2 flex-1 min-w-0">
            <p
              class="text-sm font-semibold text-gray-900 dark:text-white leading-snug"
            >
              {{ project.title }}
            </p>
            <div class="flex items-center gap-3">
              <UAvatar
                :alt="project.freelancerName"
                size="xs"
                class="bg-violet-600 shrink-0"
              />
              <span
                class="text-sm font-medium text-gray-700 dark:text-gray-300"
              >
                {{ project.freelancerName }}
              </span>
            </div>
            <div class="flex items-center gap-4">
              <span class="text-xs text-gray-400 dark:text-gray-500">
                Aceite em:
                <span class="text-gray-600 dark:text-gray-300 font-medium">{{
                  project.acceptedAt
                }}</span>
              </span>
              <span class="text-xs text-gray-400 dark:text-gray-500">
                Deadline:
                <span class="text-gray-600 dark:text-gray-300 font-medium">{{
                  project.deadline
                }}</span>
              </span>
            </div>
          </div>

          <!-- Estado + detalhes -->
          <div class="flex flex-col items-end gap-3 shrink-0">
            <UBadge
              :color="project.status === 'concluido' ? 'success' : 'warning'"
              variant="subtle"
              size="sm"
            >
              {{ project.status === "concluido" ? "Concluído" : "Em progresso" }}
            </UBadge>
            <UButton
              size="xs"
              color="neutral"
              variant="ghost"
              label="Ver detalhes"
              icon="i-lucide-arrow-up-right"
              trailing
              :to="`/app/profile/client/projects/${project.id}`"
            />
          </div>
        </div>
      </div>
    </AppLayoutProfileClient>
  </AppLayoutProfile>
</template>
