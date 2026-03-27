<script lang="ts" setup>
definePageMeta({ layout: "app" });

const reviewsCount = 5;
</script>

<template>
  <AppLayoutFreelancer>
    <!-- Section Header -->
    <div class="flex items-center gap-2 mb-4">
      <h2
        class="text-sm font-semibold text-gray-700 dark:text-gray-300 uppercase tracking-wide"
      >
        Avaliações
      </h2>
      <UBadge color="neutral" variant="subtle" size="xs">{{
        reviewsCount
      }}</UBadge>
    </div>

    <!-- Reviews List -->
    <ul class="divide-y divide-gray-100 dark:divide-gray-800">
      <AppUiCardReview name="Maria Santos" />
      <AppUiCardReview name="João Ferreira" />
      <AppUiCardReview name="Ana Rodrigues" />
      <AppUiCardReview name="Carlos Mendes" />
      <AppUiCardReview name="Sofia Lima" />
    </ul>
  </AppLayoutFreelancer>
</template>
