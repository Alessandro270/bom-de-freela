<template>
  <form
    @submit.prevent=""
    class="w-1/3 h-max border bg-slate-950 border-slate-700 rounded-md px-6 pt-4 pb-8 space-y-5"
  >
    <h1 class="mt-4 text-lg font-medium text-slate-400">FILTROS</h1>
    <hr class="text-slate-700" />
    <div class="space-y-2">
      <AppUiHeaderSide>categorias</AppUiHeaderSide>
      <ul class="space-y-1.5 lowercase">
        <AppUiCategoryItem name="1">Suporte Administrativo</AppUiCategoryItem>
        <AppUiCategoryItem name="2">Design & Criatividade</AppUiCategoryItem>
        <AppUiCategoryItem name="3">Marketing Digital</AppUiCategoryItem>
        <AppUiCategoryItem name="4">Redação & Tradução</AppUiCategoryItem>
        <AppUiCategoryItem name="5">Desenvolvimento</AppUiCategoryItem>
        <AppUiCategoryItem name="6">Consultoria</AppUiCategoryItem>
        <AppUiCategoryItem name="7">Multimédia</AppUiCategoryItem>
      </ul>
    </div>
    <hr class="text-slate-700" />
    <div class="space-y-2.5">
      <AppUiHeaderSide>habilidades</AppUiHeaderSide>
      <AppUiInputSideSearch />
    </div>
    <hr class="text-slate-700" />
    <AppUiButtonPrimary to="#">Limpar filtros</AppUiButtonPrimary>
  </form>
</template>
