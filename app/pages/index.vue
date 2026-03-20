<template>
  <div>
    <div class="h-[50vh] flex flex-col items-center justify-center">
      <h1 class="text-6xl font-extralight mb-6">
        <span class="block">Conectamos freelancers </span>
        <span
          class="inline-block bg-linear-90 from-purple-900 to-orange-600 bg-clip-text text-transparent"
        >
          aos melhores projetos</span
        >
      </h1>
      <p class="font-normal text-slate-200 mb-6">
        A plataforma que une talento e oportunidade em Angola. Publique projetos
        ou encontre trabalho com seguranca e transparencia
      </p>

      <div class="flex items-center space-x-6">
        <UiButtonCta to="/">Contrate freelancers</UiButtonCta>
        <UiButtonCta type="rev" to="/">Encontre propostas</UiButtonCta>
      </div>
    </div>
    <div class="px-20 min-h-100 flex flex-col items-center">
      <div class="text-center space-y-3 mb-10">
        <h1 class="text-3xl font-light">Procure Por categorias</h1>
        <p>Encontre o profissional perfeito para o seu projeto</p>
      </div>
      <ul class="grid grid-cols-3 gap-6 w-1/2">
        <UiCardSmall
          name="hugeicons:laptop-programming"
          title="TI e informática"
          :clients="2456"
        />
        <UiCardSmall
          name="hugeicons:laptop-programming"
          title="Design e multimédia"
          :clients="2430"
        />
        <UiCardSmall
          name="hugeicons:laptop-programming"
          title="Tradução e conteúdos"
          :clients="2545"
        />
        <UiCardSmall
          name="hugeicons:laptop-programming"
          title="Marketing e vendas"
          :clients="3212"
        />
        <UiCardSmall
          name="hugeicons:laptop-programming"
          title="Suporte administrativo"
          :clients="7642"
        />
        <UiCardSmall
          name="hugeicons:laptop-programming"
          title="Engenharia e manufatura"
          :clients="7351"
        />
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
useHead({
  title: "Bom de Freela | A plataforma de freelancing de Angola",
});
</script>
