<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileFreelancer>
      <AppUiHeaderProfile class="flex justify-between">
        <span>Habilidades</span>
        <span class="text-slate-400">(5)</span>
      </AppUiHeaderProfile>
      <ul class="*:not-last:border-b *:not-last:border-slate-700">
        <AppUiCardSkill>python</AppUiCardSkill>
        <AppUiCardSkill>javascript</AppUiCardSkill>
        <AppUiCardSkill>css</AppUiCardSkill>
        <AppUiCardSkill>html</AppUiCardSkill>
      </ul>
      <AppUiButtonSideSecondary to="/app/profile/freelancer/skills/edit">
        Editar
      </AppUiButtonSideSecondary>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
