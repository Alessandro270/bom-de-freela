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
      <slot />
    </div>
    <aside
      class="w-1/4 h-max bg-slate-950 px-6 py-7 border border-slate-700 space-y-4"
    >
      <div>
        <AppUiButtonPrimary>contratar</AppUiButtonPrimary>
      </div>
      <div>FREELANCER ACTIVITY</div>
    </aside>
  </div>
</template>
