<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutFreelancer>
    <AppUiHeaderProfile>experiencias</AppUiHeaderProfile>
    <ul class="space-y-2 *:not-last:border-b *:not-last:border-slate-700">
      <AppUiCardExperience />
      <AppUiCardExperience />
      <AppUiCardExperience />
      <AppUiCardExperience />
    </ul>
  </AppLayoutFreelancer>
</template>
