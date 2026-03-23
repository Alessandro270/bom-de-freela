<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <div class="flex space-x-10">
    <div class="w-3/4 space-y-10">
      <AppUiCardProfileFreelancer />
      <nav>
        <ul
          class="grid grid-cols-4 gap-4 *:text-center font-google bg-slate-950 py-[0.39rem] rounded-sm px-1.5"
        >
          <AppUiLinkProfileNav to="/app/freelancers/1/">
            sobre mim
          </AppUiLinkProfileNav>
          <AppUiLinkProfileNav to="/app/freelancers/1/skills">
            habilidades
          </AppUiLinkProfileNav>
          <AppUiLinkProfileNav to="/app/freelancers/1/reviews">
            reviews
          </AppUiLinkProfileNav>
          <AppUiLinkProfileNav to="/app/freelancers/1/experience">
            experiencia
          </AppUiLinkProfileNav>
        </ul>
      </nav>

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
            <li class="text-slate-400 flex items-center justify-between">
              <span>projetos em andamento:</span> <span>2</span>
            </li>
            <li class="text-slate-400 flex items-center justify-between">
              <span>projetos concluídos:</span> <span>10</span>
            </li>
          </ul>
        </div>
        <div class="space-y-2">
          <h3 class="text-slate-200 uppercase">informacao</h3>
          <ul>
            <li class="text-slate-400 flex items-center justify-between">
              <span>classificacoes:</span> <span>5</span>
            </li>
            <li class="text-slate-400 flex items-center justify-between">
              <span>ingressou:</span> <span>há 2 anos</span>
            </li>
          </ul>
        </div>
      </div>
    </aside>
  </div>
</template>
