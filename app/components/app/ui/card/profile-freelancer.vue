<template>
  <div
    class="border flex flex-col border-slate-700 px-8 py-7 space-y-6 bg-slate-950 font-google rounded-md"
  >
    <div class="flex items-center justify-between">
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

      <div class="self-start flex space-y-2 justify-start flex-col items-end">
        <AppUiButtonPrimary to="/app/freelancers/1" class="w-max px-5">
          Enviar convite
        </AppUiButtonPrimary>
        <div class="flex flex-col items-end space-y-0.5">
          <AppUiButtonDesc title="por projeto" value="500 mil Kz" />
        </div>
      </div>
    </div>
    <div class="space-x-6 text-md font-medium">
      <span class="py-1 px-3 rounded-sm bg-purple-700">FREELANCER</span>
      <span class="py-1 px-3 rounded-sm bg-purple-700">DESENVOLVIMENTO</span>
    </div>
    <hr class="text-slate-700" />

    <div class="flex flex-col space-y-4">
      <strong><i> habilidades principais:</i></strong>
      <div class="flex space-x-4 items-center">
        <AppUiButtonTag>Python</AppUiButtonTag>
        <AppUiButtonTag>Backend</AppUiButtonTag>
        <AppUiButtonTag>Pwa</AppUiButtonTag>
      </div>
    </div>
  </div>
</template>
