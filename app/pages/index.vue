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
    <div class="min-h-[50vh] flex flex-col items-center">
      <div class="text-center space-y-3 mb-10">
        <h1 class="text-3xl font-light">Procure por categorias</h1>
        <p>Encontre o profissional perfeito para o seu projeto</p>
      </div>
      <ul class="grid grid-cols-3 gap-6 w-2/3">
        <UiCardSmall
          name="hugeicons:laptop-programming"
          title="TI e informática"
          :clients="2456"
        />
        <UiCardSmall
          name="iconoir:design-pencil"
          title="Design e multimédia"
          :clients="2430"
        />
        <UiCardSmall
          name="material-symbols:language-chinese-dayi-rounded"
          title="Tradução e conteúdos"
          :clients="2545"
        />
        <UiCardSmall
          name="icon-park-outline:weixin-market"
          title="Marketing e vendas"
          :clients="3212"
        />
        <UiCardSmall
          name="solar:user-speak-bold"
          title="Suporte administrativo"
          :clients="7642"
        />
        <UiCardSmall
          name="temaki:tools"
          title="Engenharia e manufatura"
          :clients="7351"
        />
      </ul>
    </div>
    <div class="min-h-[50vh] flex flex-col items-center">
      <div class="text-center space-y-3 mb-10">
        <h1 class="text-3xl font-light">Como o Bom De Freela funciona</h1>
        <p>Simples, estruturado e eficiente</p>
      </div>
      <ul class="grid grid-cols-3 gap-4 w-2/3 font-medium">
        <UiCardStep title="Publique o seu projeto" :step="1">
          Descreva o que precisa, incluindo prazo e orçamento, para receber
          propostas de freelancers.
        </UiCardStep>

        <UiCardStep title="Candidate-se a vagas" :step="2">
          Freelancers enviam propostas para projetos conforme suas habilidades.
        </UiCardStep>

        <UiCardStep title="Dê um feedback" :step="3">
          Avalie a experiência para ajudar outros usuários e melhorar a
          plataforma.
        </UiCardStep>
      </ul>
    </div>
    <div class="min-h-[50vh] flex flex-col items-center">
      <div class="text-center space-y-3 mb-10">
        <h1 class="text-3xl font-light">O que os nossos clientes dizem</h1>
        <p>Se junte a varios clientes satisfeitos</p>
      </div>
      <ul class="grid gap-6 grid-cols-3 w-2/3">
        <UiCardTestimonial
          name="Alessandro Almeida"
          title="Deseonvolvedor backend"
          :rating="5"
        >
          “Consegui vários trabalhos rapidamente. O sistema de propostas é
          simples e ajuda bastante a conseguir novos clientes.”
        </UiCardTestimonial>
        <UiCardTestimonial name="Miguel Carlos" title="cliente" :rating="3">
          “A plataforma facilitou muito a contratação. Encontrei um profissional
          qualificado em pouco tempo e o projeto foi entregue com excelente
          qualidade.”
        </UiCardTestimonial>
        <UiCardTestimonial name="Dário Freitas" title="cliente" :rating="4">
          “O processo foi seguro e transparente. A comunicação com o freelancer
          foi clara e o resultado final superou as expectativas.”
        </UiCardTestimonial>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
useHead({
  title: "Bom de Freela | A plataforma de freelancing de Angola",
});
</script>
