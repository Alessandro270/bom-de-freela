<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutFreelancer>
    <AppUiHeaderProfile class="flex justify-between">
      <span>reviews</span>
      <span class="text-slate-300 font-medium">(5)</span>
    </AppUiHeaderProfile>
    <ul class="space-y-2 *:not-last:border-b *:not-last:border-slate-700">
      <AppUiCardReview name="Alessandro Almeida" />
      <AppUiCardReview name="Alessandro Almeida" />
      <AppUiCardReview name="Alessandro Almeida" />
      <AppUiCardReview name="Alessandro Almeida" />
    </ul>
  </AppLayoutFreelancer>
</template>
