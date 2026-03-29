<script setup lang="ts">
import type { ButtonProps } from "@nuxt/ui";

useHead({
  title: "Bom de Freela | A plataforma de freelancing de Angola",
});

const links = ref<ButtonProps[]>([
  {
    label: "Encontre trabalho",
    color: "primary",
  },
  {
    label: "Cadastre-se já",
    color: "neutral",
    variant: "subtle",
    trailingIcon: "i-lucide-arrow-right",
  },
]);

const cards = computed(() => [
  {
    title: "Desenvolvimento",
    description:
      "Projetos relacionados ao desenvolvimento de software, aplicações web, mobile e sistemas personalizados.",
    icon: "i-lucide-code",
    to: "/categorias/desenvolvimento",
  },
  {
    title: "Design & Criatividade",
    description:
      "Serviços de design gráfico, UI/UX, branding, ilustração e criação visual para produtos digitais.",
    icon: "i-lucide-palette",
    to: "/categorias/design-criatividade",
  },
  {
    title: "Marketing Digital",
    description:
      "Campanhas de marketing, gestão de redes sociais, SEO, publicidade online e estratégias digitais.",
    icon: "i-lucide-megaphone",
    to: "/categorias/marketing-digital",
  },
  {
    title: "Redação & Tradução",
    description:
      "Produção de conteúdo, revisão textual, copywriting e serviços profissionais de tradução.",
    icon: "i-lucide-file-text",
    to: "/categorias/redacao-traducao",
  },
  {
    title: "Suporte Administrativo",
    description:
      "Assistência virtual, entrada de dados, organização de documentos e tarefas administrativas.",
    icon: "i-lucide-briefcase",
    to: "/categorias/suporte-administrativo",
  },
  {
    title: "Consultoria",
    description:
      "Serviços especializados de consultoria em negócios, tecnologia, finanças e gestão de projetos.",
    icon: "i-lucide-lightbulb",
    to: "/categorias/consultoria",
  },
]);
</script>

<template>
  <div>
    <section class="px-8 py-6">
      <UPageCTA
        title="Conectando Jovens talentos com sonhos"
        description="Conectamos empresas e profissionais talentosos em Angola."
        variant="naked"
        orientation="horizontal"
        :links="links"
      >
        <img
          src="~/assets/img/work.jpg"
          class="rounded-sm w-full h-full object-cover"
        />
      </UPageCTA>
    </section>
    <section class="px-8 py-30 space-y-10 flex space-x-10">
      <div class="w-2/5">
        <img src="~/assets/img/my_app.svg" class="h-full" alt="app" />
      </div>
      <div class="w-3/5 space-y-6 flex flex-col">
        <div>
          <span class="text-md uppercase font-semibold text-purple-600"
            >categorias</span
          >
          <h2 class="text-3xl font-bold">
            Explore as categorias mais populares
          </h2>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mt-6">
          <UPageCard
            v-for="card in cards"
            variant="ghost"
            :key="card.title"
            :title="card.title"
            :description="card.description"
            :icon="card.icon"
            :to="card.to"
          />
        </div>
      </div>
    </section>
  </div>
</template>
