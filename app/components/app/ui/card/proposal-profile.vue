<template>
  <div class="py-3">
    <div class="flex justify-between items-center">
      <h3 class="text-md uppercase font-medium">Titulo</h3>
      <AppUiButtonDesc title="postado em" value="12/03/2023" />
    </div>

    <div class="flex justify-between items-center mb-4">
      <UiRating :value="4" />
      <AppUiButtonDesc title="propostas" value="5" />
    </div>
    <div class="flex mb-4 items-center justify-between">
      <div class="flex space-x-4">
        <i class="text-sm font-medium"> tags:</i>
        <div class="flex space-x-4 items-center">
          <AppUiButtonTag>Python</AppUiButtonTag>
          <AppUiButtonTag>Backend</AppUiButtonTag>
          <AppUiButtonTag>Pwa</AppUiButtonTag>
        </div>
      </div>
      <AppUiLinkNav class="w-max text-sm" to="/app/profile/client/proposals/1">
        ver proposta
      </AppUiLinkNav>
    </div>
  </div>
</template>
