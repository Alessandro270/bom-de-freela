<template>
  <li
    class="border flex flex-col border-slate-700 px-8 py-7 space-y-3 bg-slate-950 font-google rounded-md"
  >
    <div class="flex items-center justify-between">
      <h1 class="text-5xl capitalize">titulo</h1>
      <div class="flex space-y-2 justify-center flex-col items-end">
        <AppUiButtonPrimary class="w-max px-5">
          fazer proposta
        </AppUiButtonPrimary>
        <div
          class="flex flex-col space-x-2 font-medium text-slate-400 items-center"
        >
          <AppUiButtonDesc title="preco inicial" value="500 mil Kz" />
        </div>
      </div>
    </div>
    <div class="space-x-4">
      <UiRating :value="0" class="mb-2" />
      <AppUiButtonDesc title="publicado em" value="12" />
      <AppUiButtonDesc title="propostas" value="10" />
    </div>
    <div class="space-y-1">
      <AppUiHeaderSide> Descricao</AppUiHeaderSide>
      <p class="text-justify">
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Illum sapiente
        quia numquam hic. Consequatur vitae sit harum impedit esse, sapiente
        aspernatur expedita. Obcaecati, voluptatem deleniti? Minima quis tenetur
        maiores sint.
        <span class="inline-block underline text-slate-300">ver mais</span>
      </p>
    </div>
    <div class="flex justify-between">
      <div class="flex space-x-4 items-center">
        <AppUiButtonAvatar name="Alessandro Almeida" />
        <div class="space-y-0.5 flex flex-col">
          <strong>Alessandro Almeida</strong>
          <i class="text-sm">ultima proposta: ha 7 horas</i>
        </div>
      </div>
      <div class="flex items-start space-x-4">
        <strong><i> tags:</i></strong>
        <div class="flex space-x-4 items-center">
          <AppUiButtonTag>Python</AppUiButtonTag>
          <AppUiButtonTag>Backend</AppUiButtonTag>
          <AppUiButtonTag>Pwa</AppUiButtonTag>
          <span
            class="flex items-center rounded-sm h-6 w-6 transition cursor-pointer justify-center hover:bg-purple-700"
          >
            <Icon
              name="material-symbols:add-2"
              class="leading-5 text-slate-50"
            />
          </span>
        </div>
      </div>
    </div>
  </li>
</template>
