<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileFreelancer>
      <!-- Cabeçalho da secção -->
      <div class="flex items-center justify-between mb-4">
        <div class="flex items-center gap-2">
          <h2 class="text-sm font-semibold text-gray-700 dark:text-gray-300 uppercase tracking-wide">
            Avaliações
          </h2>
          <UBadge color="neutral" variant="subtle" size="xs">5</UBadge>
        </div>
      </div>

      <!-- Lista de avaliações -->
      <ul class="divide-y divide-gray-100 dark:divide-gray-800">
        <AppUiCardReview name="Alessandro Almeida" />
        <AppUiCardReview name="Alessandro Almeida" />
        <AppUiCardReview name="Alessandro Almeida" />
        <AppUiCardReview name="Alessandro Almeida" />
      </ul>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
