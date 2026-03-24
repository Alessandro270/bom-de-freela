<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileFreelancer>
      <AppUiHeaderProfile class="flex justify-between">
        <span>Experiencia</span>
        <span class="text-slate-400">(5)</span>
      </AppUiHeaderProfile>
      <ul class="*:not-last:border-b *:not-last:border-slate-700">
        <AppUiCardExperience />
        <AppUiCardExperience />
        <AppUiCardExperience />
        <AppUiCardExperience />
      </ul>
      <AppUiButtonSideSecondary>Editar</AppUiButtonSideSecondary>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
