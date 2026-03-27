<script lang="ts" setup>
definePageMeta({ layout: "app" });

const reviewsCount = 18;
</script>

<template>
  <AppLayoutClientPublic>
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

    <!-- Reviews List (from freelancers who worked with this client) -->
    <ul class="divide-y divide-gray-100 dark:divide-gray-800">
      <AppUiCardReview name="Freelancer · Pedro Alves" />
      <AppUiCardReview name="Freelancer · Ana Costa" />
      <AppUiCardReview name="Freelancer · Miguel Santos" />
      <AppUiCardReview name="Freelancer · Carla Mendes" />
    </ul>
  </AppLayoutClientPublic>
</template>
