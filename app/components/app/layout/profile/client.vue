<template>
  <div class="space-y-6 font-google max-w-5xl mx-auto">
    <div
      class="bg-slate-950 flex justify-between items-start rounded-md px-6 py-7 space-y-4"
    >
      <div class="flex justify-between w-full">
        <div class="space-x-8 flex">
          <AppUiButtonSquareAvatar name="Alessandro Almeida" />
          <div class="flex space-y-0.5 flex-col">
            <h1 class="text-3xl text-slate-200">Alessandro Almeida</h1>
            <span class="text-xl font-medium text-slate-400"> Cliente </span>
            <div class="flex h-6 items-center space-x-2">
              <UiRating :value="4" />
            </div>
          </div>
        </div>
        <div class="items-start h-max space-x-4 w-1/5">
          <AppUiButtonSideDesc title="Membro desde" value="2023" />
        </div>
      </div>
    </div>
    <AppUiNavBar
      :items="[
        { to: '/app/profile/client/', label: 'Sobre mim' },
        { to: '/app/profile/client/proposals', label: 'Propostas' },
        { to: '/app/profile/client/reviews', label: 'Avaliações' },
      ]"
    />
    <div class="bg-slate-950 rounded-md px-6 py-7 space-y-4">
      <slot />
    </div>
  </div>
</template>
