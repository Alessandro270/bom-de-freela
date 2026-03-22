<template>
  <li
    class="border border-slate-700 px-8 py-7 space-y-3 bg-slate-950 font-google rounded-md"
  >
    <div class="flex items-center justify-between">
      <h1 class="text-5xl capitalize">titulo</h1>
      <div class="flex space-y-2 justify-center flex-col items-end">
        <AppUiButtonPrimary class="w-max px-5">
          fazer proposta
        </AppUiButtonPrimary>
        <span class="inline-block text-sm">
          <strong>preco inicial:</strong> <i>500 mil Kz</i>
        </span>
      </div>
    </div>
    <div class="space-x-4">
      <i>publicado em: 12</i>
      <i>propostas: 10</i>
    </div>
    <div class="space-y-1">
      <AppUiHeaderSide> Descricao</AppUiHeaderSide>
      <p class="text-justify">
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Illum sapiente
        quia numquam hic. Consequatur vitae sit harum impedit esse, sapiente
        aspernatur expedita. Obcaecati, voluptatem deleniti? Minima quis tenetur
        maiores sint.
      </p>
    </div>
    <div class="flex space-x-4">
      <strong><i> tags:</i></strong>
      <div class="flex space-x-4">
        <AppUiButtonTag>Python</AppUiButtonTag>
        <AppUiButtonTag>Backend</AppUiButtonTag>
        <AppUiButtonTag>Pwa</AppUiButtonTag>
        <Icon name="material-symbols:add-2" />
      </div>
    </div>
    <div class="flex space-x-4 items-center">
      <AppUiButtonAvatar name="Alessandro Almeida" />
      <div class="space-y-0.5 flex flex-col">
        <strong>Alessandro Almeida</strong>
        <i class="text-sm">ultima proposta: ha 7 horas</i>
      </div>
    </div>
    <div class="flex space-x-2 items-center">
      <strong><i>reviews: </i></strong> <UiRating :value="0" />
    </div>
  </li>
</template>
