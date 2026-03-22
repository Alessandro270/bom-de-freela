<template>
  <li class="border px-5 py-7 bg-slate-950 rounded-md">
    <div class="flex justify-between">
      <h1 class="text-5xl capitalize">titulo</h1>
      <div class="flex space-y-2 justify-center flex-col items-end">
        <AppUiButtonPrimary class="w-max px-5"
          >fazer proposta</AppUiButtonPrimary
        >
        <span class="inline-block text-sm">
          <strong>preco inicial:</strong> <i>500 mil Kz</i>
        </span>
      </div>
    </div>
    <div>
      <span>publicado em: 12</span>
      <span>propostas: 10</span>
    </div>
    <div>
      <h3>Descricao</h3>
      <p>
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Illum sapiente
        quia numquam hic. Consequatur vitae sit harum impedit esse, sapiente
        aspernatur expedita. Obcaecati, voluptatem deleniti? Minima quis tenetur
        maiores sint.
      </p>
    </div>
    <div>
      <h3>tags</h3>
      <div>
        <span>1</span><span>2</span><span>3</span>
        <Icon name="material-symbols:add-2" />
      </div>
    </div>
    <div>
      <AppUiButtonAvatar name="Alessandro Almeida" />
      <span>ultima proposta: ha 7 horas</span>
    </div>
    <div><span>reviews: </span> <UiRating :value="0" /></div>
  </li>
</template>
