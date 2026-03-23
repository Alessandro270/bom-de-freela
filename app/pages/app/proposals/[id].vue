<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <div class="font-google flex space-x-10">
    <div class="w-3/4">
      <div class="space-y-2">
        <h1 class="text-2xl font-medium">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
        </h1>
        <div class="flex items-center gap-2">
          <UiRating :value="5" />
          <AppUiButtonDesc title="Avaliações" value="(5)" />
          <AppUiButtonDesc title="Postado em" value="23/03/2026" />
        </div>
      </div>

      <div class="mt-4 bg-slate-950 space-y-4 px-6 py-7 rounded-sm">
        <h2 class="text-xl uppercase font-medium flex justify-between">
          <span>Descrição</span>
          <span>500,000.00 kz</span>
        </h2>
        <p class="text-slate-300 text-justify">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
        </p>
        <div class="flex flex-col space-y-2">
          <AppUiButtonDesc
            title="Categoria"
            value="Desenvolvimento de Software"
          />
          <AppUiButtonDesc title="Subcategoria" value="Desenvolvimento Web" />
          <AppUiButtonDesc title="Prazo de entrega" value="30/03/2026" />
        </div>
        <div class="space-y-3">
          <span class="text-slate-100 inline-block font-medium"
            >Habilidades necessárias</span
          >
          <div class="space-x-3">
            <AppUiButtonTag>python</AppUiButtonTag>
            <AppUiButtonTag>javascript</AppUiButtonTag>
            <AppUiButtonTag>java</AppUiButtonTag>
          </div>
        </div>
      </div>
    </div>
    <aside class="w-1/4 bg-slate-950 px-6 py-7 h-max rounded-sm space-y-4">
      <div class="space-y-4 border-b border-slate-700 pb-4">
        <h3 class="text-slate-200 font-semibold uppercase">Actividade</h3>
        <div class="space-y-2">
          <AppUiButtonSideDesc title="propostas enviadas" value="2" />
          <AppUiButtonSideDesc title="Ultima proposta" value="há 2 horas" />
        </div>
      </div>
      <div class="space-y-3">
        <div class="flex h-max items-center space-x-4">
          <NuxtLink
            to="/app/proposals"
            class="h-10 w-10 rounded-sm bg-purple-700 flex items-center justify-center font-semibold text-slate-50"
          >
            AA
          </NuxtLink>
          <div class="text-slate-200 h-full font-semibold space-y-1 uppercase">
            <span class="text-sm capitalize inline-block"
              >Alessandro Almeida</span
            >
            <UiRating :value="5" />
          </div>
        </div>

        <div>
          <AppUiButtonSideDesc title="Propostas publicadas" value="5" />
          <AppUiButtonSideDesc title="Membro desde" value="2023" />
        </div>
      </div>
    </aside>
  </div>
</template>
