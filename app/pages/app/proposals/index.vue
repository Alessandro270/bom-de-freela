<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <div class="relative flex min-h-screen space-x-10">
    <AppLayoutCategoryBar />

    <main class="w-3/4 flex space-y-2 flex-col">
      <AppUiInputSearch />

      <div class="space-y-4 text-slate-400">
        <ul class="font-medium">
          Nenhum filtro aplicado..
        </ul>
        <ul class="space-y-8">
          <AppUiCardProposal />
          <AppUiCardProposal />
          <AppUiCardProposal />
        </ul>
      </div>
    </main>
  </div>
</template>
