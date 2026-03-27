<script lang="ts" setup>
definePageMeta({ layout: "app" });
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
            Propostas
          </h2>
          <UBadge color="neutral" variant="subtle" size="xs">2</UBadge>
        </div>
        <UButton
          size="xs"
          color="primary"
          variant="soft"
          icon="i-lucide-plus"
          label="Nova proposta"
          to="/app/profile/client/proposals/new"
        />
      </div>

      <!-- Lista de propostas -->
      <div class="divide-y divide-gray-100 dark:divide-gray-800">
        <AppUiCardProposalProfile />
        <AppUiCardProposalProfile />
      </div>
    </AppLayoutProfileClient>
  </AppLayoutProfile>
</template>
