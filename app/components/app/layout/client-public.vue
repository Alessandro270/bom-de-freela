<script lang="ts" setup>
const route = useRoute();
const id = computed(() => (route.params.id as string) ?? "1");

const navItems = computed(() => [
  { to: `/app/clients/${id.value}/`, label: "Sobre mim" },
  { to: `/app/clients/${id.value}/projects`, label: "Projetos" },
  { to: `/app/clients/${id.value}/reviews`, label: "Avaliações" },
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
              class="h-20 w-20 rounded-xl bg-blue-600 flex items-center justify-center text-2xl font-bold text-white select-none shrink-0"
            >
              AA
            </div>
            <div class="space-y-1">
              <h1 class="text-2xl font-bold text-gray-900 dark:text-white">
                Alessandro Almeida
              </h1>
              <p class="text-base font-medium text-gray-500 dark:text-gray-400">
                Cliente · Empresa Individual
              </p>
              <div class="flex items-center gap-1.5">
                <UiRating :value="4" />
                <span class="text-xs text-gray-400 dark:text-gray-500"
                  >(18 avaliações)</span
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
              icon="i-lucide-shield-check"
            >
              Pagamento Verificado
            </UBadge>
          </div>
        </div>

        <USeparator />

        <!-- Sectors -->
        <div class="flex items-center gap-2 flex-wrap">
          <span
            class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide shrink-0"
          >
            Setores:
          </span>
          <UBadge color="neutral" variant="subtle" size="sm">Tecnologia</UBadge>
          <UBadge color="neutral" variant="subtle" size="sm">Startups</UBadge>
          <UBadge color="neutral" variant="subtle" size="sm">E-commerce</UBadge>
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
              icon="i-lucide-folder-open"
              label="Ver Projetos Abertos"
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
                    >Projetos publicados</span
                  >
                  <span class="font-semibold text-gray-900 dark:text-white"
                    >12</span
                  >
                </div>
                <div class="flex justify-between text-sm">
                  <span class="text-gray-500 dark:text-gray-400"
                    >Em andamento</span
                  >
                  <span class="font-semibold text-gray-900 dark:text-white"
                    >3</span
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
                  <span class="text-gray-500 dark:text-gray-400">Gasto total</span>
                  <span class="font-semibold text-gray-900 dark:text-white"
                    >2.5M Kz</span
                  >
                </div>
                <div class="flex justify-between text-sm">
                  <span class="text-gray-500 dark:text-gray-400">Classificação</span>
                  <span class="font-semibold text-gray-900 dark:text-white"
                    >4.8</span
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
