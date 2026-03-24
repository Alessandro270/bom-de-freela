<script lang="ts" setup>
import App from "~/app.vue";

definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutProfileClient>
    <AppUiHeaderProfile class="flex items-center justify-between">
      <span>propostas</span>
      <span class="text-slate-400">(5)</span>
    </AppUiHeaderProfile>
    <div class="*:not-last:border-b *:not-last:border-slate-700">
      <AppUiCardProposalProfile />
      <AppUiCardProposalProfile />
    </div>
  </AppLayoutProfileClient>
</template>
