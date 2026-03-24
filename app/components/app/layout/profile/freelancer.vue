<template>
  <div class="space-y-6 font-google w-5xl mx-auto">
    <div
      class="bg-slate-950 flex justify-between items-start rounded-md px-6 py-7 space-y-4"
    >
      <div class="flex justify-between items-start w-full h-full">
        <div class="space-x-8 flex">
          <AppUiButtonSquareAvatar name="Alessandro Almeida" />
          <div class="flex space-y-0.5 flex-col">
            <h1 class="text-3xl text-slate-200">Alessandro Almeida</h1>
            <span class="text-xl font-medium text-slate-400">
              Desenvolvedor backend
            </span>
            <div class="flex h-6 items-center space-x-2">
              <UiRating :value="4" />
            </div>
          </div>
        </div>
        <div class="flex flex-col w-1/5 justify-between h-26 items-end">
          <AppUiButtonSideDesc title="Membro desde" value="2023" />
          <div class="flex space-x-4">
            <AppUiButtonSideSecondary to="/app/profile/client/edit">
              Editar
            </AppUiButtonSideSecondary>
          </div>
        </div>
      </div>
    </div>
    <AppUiNavBar
      :items="[
        { to: '/app/profile/freelancer/', label: 'Sobre mim' },
        { to: '/app/profile/freelancer/projects', label: 'Projetos' },
        { to: '/app/profile/freelancer/reviews', label: 'Avaliações' },
        { to: '/app/profile/freelancer/proposals', label: 'Propostas' },
      ]"
    />
    <div class="bg-slate-950 min-h-60 rounded-md px-6 py-7 space-y-4">
      <slot />
    </div>
  </div>
</template>
