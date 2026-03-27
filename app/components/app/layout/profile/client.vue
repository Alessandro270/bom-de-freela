<template>
  <div class="space-y-4 w-5xl mx-auto">
    <!-- Hero card: avatar + nome + rating + ação -->
    <UCard>
      <div class="flex items-start justify-between gap-6">
        <!-- Avatar + nome + rating -->
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
              Cliente
            </p>
            <UiRating :value="4" />
          </div>
        </div>

        <!-- Meta: membro desde + postar proposta -->
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
          <UButton
            color="primary"
            variant="solid"
            size="sm"
            icon="i-lucide-plus"
            label="Postar Proposta"
            to="/app/profile/client/proposals/new"
          />
        </div>
      </div>
    </UCard>

    <!-- Navegação entre secções -->
    <AppUiNavBar
      :items="[
        { to: '/app/profile/client/', label: 'Sobre mim' },
        { to: '/app/profile/client/proposals', label: 'Propostas' },
        { to: '/app/profile/client/reviews', label: 'Avaliações' },
      ]"
    />

    <!-- Conteúdo da secção activa -->
    <UCard>
      <slot />
    </UCard>
  </div>
</template>
