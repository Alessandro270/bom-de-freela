<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutFreelancer>
    <AppUiHeaderProfile class="flex justify-between">
      <span>habilidades</span>
      <span class="text-slate-300 font-medium">(4)</span>
    </AppUiHeaderProfile>
    <ul class="*:not-last:border-b *:not-last:border-slate-700">
      <AppUiCardSkill :value="4">python</AppUiCardSkill>
      <AppUiCardSkill :value="5">javascript</AppUiCardSkill>
      <AppUiCardSkill :value="5">css</AppUiCardSkill>
      <AppUiCardSkill :value="4">html</AppUiCardSkill>
    </ul>
  </AppLayoutFreelancer>
</template>
