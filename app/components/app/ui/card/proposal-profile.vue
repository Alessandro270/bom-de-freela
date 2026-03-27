<template>
  <div class="py-4 flex items-start justify-between gap-4">
    <!-- Info -->
    <div class="space-y-2 flex-1 min-w-0">
      <p class="text-sm font-semibold text-gray-900 dark:text-white">
        Título da proposta
      </p>
      <div class="flex items-center gap-3 flex-wrap">
        <UiRating :value="4" />
        <span class="text-xs text-gray-400 dark:text-gray-500">
          Postado em:
          <span class="text-gray-600 dark:text-gray-300 font-medium">
            12/03/2023
          </span>
        </span>
        <span class="text-xs text-gray-400 dark:text-gray-500">
          Propostas:
          <span class="text-gray-600 dark:text-gray-300 font-medium">5</span>
        </span>
      </div>
      <div class="flex items-center gap-2 flex-wrap">
        <span
          class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
        >
          Tags:
        </span>
        <UBadge color="primary" variant="subtle" size="xs">Python</UBadge>
        <UBadge color="primary" variant="subtle" size="xs">Backend</UBadge>
        <UBadge color="primary" variant="subtle" size="xs">Pwa</UBadge>
      </div>
    </div>

    <!-- Link -->
    <UButton
      size="xs"
      color="neutral"
      variant="ghost"
      label="Ver proposta"
      icon="i-lucide-arrow-up-right"
      trailing
      to="/app/profile/client/proposals/1"
    />
  </div>
</template>
