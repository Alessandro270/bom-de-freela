<template>
  <li
    class="border flex flex-col border-slate-700 px-8 py-7 space-y-3 bg-slate-950 font-google rounded-md"
  >
    <div class="flex items-center justify-between">
      <div class="space-x-8 flex">
        <div
          class="py-8 min-w-24 rounded-md flex items-center justify-center font-bold text-4xl capitalize text-slate-50 bg-purple-700"
        >
          <span class="inline-block leading-5"> AA </span>
        </div>
        <div class="flex space-y-0.5 flex-col">
          <span class="text-2xl text-slate-200">Alessandro Almeida</span>
          <span class="text-xl font-medium text-slate-400">
            Desenvolvedor backend
          </span>
          <div class="flex h-6 items-center space-x-2">
            <!-- <span class="inline-block font-bold leading-6">4.5</span>
            <Icon
              name="codicon:star-full"
              class="text-sm text-amber-500 -mt-0.5"
            /> -->
            <UiRating :value="4" />
          </div>
        </div>
      </div>
      <div class="self-start flex space-y-2 justify-start flex-col items-end">
        <AppUiButtonPrimary class="w-max px-5"> ver perfil </AppUiButtonPrimary>
        <div class="flex flex-col items-end space-y-0.5">
          <AppUiButtonDesc title="por projeto" value="500 mil Kz" />
          <AppUiButtonDesc title="projetos" value="12" />
        </div>
      </div>
    </div>

    <div class="space-y-1">
      <AppUiHeaderSide>Sobre mim</AppUiHeaderSide>
      <p class="text-justify">
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Illum sapiente
        quia numquam hic. Consequatur vitae sit harum impedit esse, sapiente
        aspernatur expedita. Obcaecati, voluptatem deleniti? Minima quis tenetur
        maiores sint.
        <span class="inline-block underline text-slate-300">ver mais</span>
      </p>
    </div>
    <div class="flex space-x-4">
      <strong><i> habilidades:</i></strong>
      <div class="flex space-x-4 items-center">
        <AppUiButtonTag>Python</AppUiButtonTag>
        <AppUiButtonTag>Backend</AppUiButtonTag>
        <AppUiButtonTag>Pwa</AppUiButtonTag>
        <span
          class="flex items-center rounded-sm h-6 w-6 transition cursor-pointer justify-center hover:bg-purple-700"
        >
          <Icon name="material-symbols:add-2" class="leading-5 text-slate-50" />
        </span>
      </div>
    </div>
  </li>
</template>
