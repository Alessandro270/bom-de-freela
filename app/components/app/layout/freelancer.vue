<script lang="ts" setup>
const tags = ref<string[]>(["Python", "Backend", "PWA"]);
const route = useRoute();
const id = computed(() => (route.params.id as string) ?? "1");

const navItems = computed(() => [
  { to: `/app/freelancers/${id.value}/`, label: "Sobre mim" },
  { to: `/app/freelancers/${id.value}/skills`, label: "Habilidades" },
  { to: `/app/freelancers/${id.value}/reviews`, label: "Avaliações" },
  { to: `/app/freelancers/${id.value}/experience`, label: "Experiência" },
]);
</script>

<template>
  <div class="space-y-5 max-w-5xl mx-auto">
    <!-- Breadcrumb Navigation -->
    <AppUiNavBreadcrumb />

    <div class="space-y-6">
    <!-- Hero Card -->
    <UCard>
      <div class="flex flex-col gap-4">
        <div class="flex items-start justify-between gap-6">
          <!-- Avatar + Info -->
          <div class="flex items-center gap-6">
            <div
              class="h-20 w-20 rounded-xl bg-violet-600 flex items-center justify-center text-2xl font-bold text-white select-none shrink-0"
            >
              AA
            </div>
            <div class="space-y-1">
              <h1 class="text-2xl font-bold text-gray-900 dark:text-white">
                Alessandro Almeida
              </h1>
              <p class="text-base font-medium text-gray-500 dark:text-gray-400">
                Desenvolvedor backend
              </p>
              <div class="flex items-center gap-1.5">
                <UiRating :value="4" />
                <span class="text-xs text-gray-400 dark:text-gray-500"
                  >(24 avaliações)</span
                >
              </div>
            </div>
          </div>

          <!-- Meta -->
          <div class="flex flex-col items-end gap-3 shrink-0">
            <div class="text-right">
              <p
                class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                Membro desde
              </p>
              <p class="text-sm font-semibold text-gray-900 dark:text-white">
                2023
              </p>
            </div>
            <UBadge
              color="success"
              variant="subtle"
              size="sm"
              icon="i-lucide-check-circle"
            >
              Verificado
            </UBadge>
          </div>
        </div>

        <USeparator />

        <!-- Skills -->
        <div class="flex items-center gap-2 flex-wrap">
          <span
            class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide shrink-0"
          >
            Habilidades:
          </span>
          <UBadge
            v-for="tag in tags"
            :key="tag"
            color="primary"
            variant="subtle"
            size="sm"
          >
            {{ tag }}
          </UBadge>
        </div>
      </div>
    </UCard>

    <!-- Body: Main + Sidebar -->
    <div class="flex gap-6 items-start">
      <!-- Main -->
      <div class="flex-1 min-w-0 space-y-4">
        <AppUiNavBar :items="navItems" />
        <UCard>
          <slot />
        </UCard>
      </div>

      <!-- Sidebar -->
      <aside class="w-64 shrink-0">
        <UCard class="sticky top-6">
          <div class="space-y-5">
            <UButton
              block
              size="md"
              color="primary"
              variant="solid"
              icon="i-lucide-send"
              label="Contratar"
            />

            <USeparator />

            <div class="space-y-2">
              <p
                class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                Atividade
              </p>
              <div class="space-y-1.5">
                <div class="flex justify-between text-sm">
                  <span class="text-gray-500 dark:text-gray-400"
                    >Em andamento</span
                  >
                  <span class="font-semibold text-gray-900 dark:text-white"
                    >2</span
                  >
                </div>
                <div class="flex justify-between text-sm">
                  <span class="text-gray-500 dark:text-gray-400">Concluídos</span>
                  <span class="font-semibold text-gray-900 dark:text-white"
                    >10</span
                  >
                </div>
              </div>
            </div>

            <USeparator />

            <div class="space-y-2">
              <p
                class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                Informação
              </p>
              <div class="space-y-1.5">
                <div class="flex justify-between text-sm">
                  <span class="text-gray-500 dark:text-gray-400">Classificação</span>
                  <span class="font-semibold text-gray-900 dark:text-white"
                    >5.0</span
                  >
                </div>
                <div class="flex justify-between text-sm">
                  <span class="text-gray-500 dark:text-gray-400">Desde</span>
                  <span class="font-semibold text-gray-900 dark:text-white"
                    >2023</span
                  >
                </div>
              </div>
            </div>
          </div>
        </UCard>
      </aside>
    </div>
    </div>
  </div>
</template>
