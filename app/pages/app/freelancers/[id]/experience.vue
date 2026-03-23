<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutFreelancer>
    <AppUiHeaderProfile class="flex justify-between">
      <span>experiencias</span>
      <span class="text-slate-400"> (5)</span>
    </AppUiHeaderProfile>
    <ul class="space-y-2 *:not-last:border-b *:not-last:border-slate-700">
      <AppUiCardExperience />
      <AppUiCardExperience />
      <AppUiCardExperience />
      <AppUiCardExperience />
    </ul>
  </AppLayoutFreelancer>
</template>
