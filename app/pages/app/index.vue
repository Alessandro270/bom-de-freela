<script lang="ts" setup>
definePageMeta({ layout: "app" });

const stats = [
  {
    label: "Propostas activas",
    value: "8",
    icon: "i-lucide-file-text",
    color: "text-blue-500",
    bg: "bg-blue-50 dark:bg-blue-950/40",
  },
  {
    label: "Projectos em curso",
    value: "3",
    icon: "i-lucide-folder-open",
    color: "text-violet-500",
    bg: "bg-violet-50 dark:bg-violet-950/40",
  },
  {
    label: "Notificações",
    value: "4",
    icon: "i-lucide-bell",
    color: "text-amber-500",
    bg: "bg-amber-50 dark:bg-amber-950/40",
  },
  {
    label: "Avaliação média",
    value: "4.8",
    icon: "i-lucide-star",
    color: "text-green-500",
    bg: "bg-green-50 dark:bg-green-950/40",
  },
];

const quickLinks = [
  {
    label: "Explorar propostas",
    description: "Encontra projectos adequados ao teu perfil",
    icon: "i-lucide-search",
    to: "/app/proposals",
  },
  {
    label: "Os meus freelancers",
    description: "Consulta e contrata profissionais",
    icon: "i-lucide-users",
    to: "/app/freelancers",
  },
  {
    label: "Notificações",
    description: "Vê todas as tuas notificações pendentes",
    icon: "i-lucide-bell",
    to: "/app/notifications",
  },
];
</script>

<template>
  <AppLayoutWrapper>
    <div class="space-y-6">
      <!-- Page header -->
      <div>
        <h1 class="text-xl font-bold text-gray-900 dark:text-white">
          Bem-vindo de volta 👋
        </h1>
        <p class="text-sm text-gray-500 dark:text-gray-400 mt-1">
          Aqui tens uma visão geral da tua actividade na plataforma.
        </p>
      </div>

      <!-- Quick stats -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
        <UCard v-for="stat in stats" :key="stat.label">
          <div class="flex items-center gap-4">
            <div
              class="h-10 w-10 rounded-lg flex items-center justify-center shrink-0"
              :class="stat.bg"
            >
              <UIcon :name="stat.icon" class="h-5 w-5" :class="stat.color" />
            </div>
            <div>
              <p
                class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                {{ stat.label }}
              </p>
              <p class="text-xl font-bold text-gray-900 dark:text-white">
                {{ stat.value }}
              </p>
            </div>
          </div>
        </UCard>
      </div>

      <!-- Quick links -->
      <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
        <UCard
          v-for="link in quickLinks"
          :key="link.label"
          class="hover:ring-1 hover:ring-primary-300 dark:hover:ring-primary-700 transition-all"
        >
          <NuxtLink :to="link.to" class="flex items-center gap-3">
            <div
              class="h-9 w-9 rounded-lg bg-primary-50 dark:bg-primary-950/40 flex items-center justify-center shrink-0"
            >
              <UIcon :name="link.icon" class="h-5 w-5 text-primary-500" />
            </div>
            <div class="flex-1 min-w-0">
              <p class="text-sm font-semibold text-gray-900 dark:text-white">
                {{ link.label }}
              </p>
              <p class="text-xs text-gray-500 dark:text-gray-400 truncate">
                {{ link.description }}
              </p>
            </div>
            <UIcon
              name="i-lucide-arrow-right"
              class="h-4 w-4 text-gray-400 shrink-0"
            />
          </NuxtLink>
        </UCard>
      </div>
    </div>
  </AppLayoutWrapper>
</template>
