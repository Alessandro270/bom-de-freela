<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <div class="flex space-x-10">
    <div class="w-3/4 space-y-10">
      <AppUiCardProfileFreelancer />
      <AppUiNavBar
        :items="[
          { to: '/app/freelancers/1/', label: 'Sobre mim' },
          { to: '/app/freelancers/1/skills', label: 'Habilidades' },
          { to: '/app/freelancers/1/reviews', label: 'Avaliações' },
          { to: '/app/freelancers/1/experience', label: 'Experiência' },
        ]"
      />

      <div
        class="bg-slate-950 space-y-3 rounded-sm border border-slate-700 px-6 py-7"
      >
        <slot />
      </div>
    </div>
    <aside
      class="w-1/4 h-max bg-slate-950 px-6 py-7 border border-slate-700 space-y-4"
    >
      <div>
        <AppUiButtonPrimary>contratar</AppUiButtonPrimary>
      </div>
      <div class="font-google font-medium text-md text-slate-400 space-y-4">
        <div class="space-y-2">
          <h3 class="text-slate-200 uppercase">Actividade</h3>
          <ul class="space-y-0.5">
            <AppUiButtonSideDesc title="projetos em andamento" value="2" />
            <AppUiButtonSideDesc title="projetos concluídos" value="10" />
          </ul>
        </div>
        <div class="space-y-2">
          <h3 class="text-slate-200 uppercase">informacao</h3>
          <ul>
            <AppUiButtonSideDesc title="Classificações" value="5" />
            <AppUiButtonSideDesc title="Membro desde" value="2023" />
          </ul>
        </div>
      </div>
    </aside>
  </div>
</template>
