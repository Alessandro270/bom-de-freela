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

const feats = computed(() => [
  {
    title: "Publicação de Serviços",
    description:
      "Clientes podem criar e divulgar os suas propostas de forma simples, alcançando profissionais em todo o território nacional.",
    icon: "i-lucide-megaphone",
  },
  {
    title: "Contratação Segura",
    description:
      "Clientes podem contratar freelancers com transparência, avaliando perfis, experiências e classificações antes de fechar um trabalho.",
    icon: "i-lucide-shield-check",
  },
  {
    title: "Sistema de Avaliações",
    description:
      "Após cada projeto, clientes e freelancers podem avaliar a experiência, promovendo confiança e qualidade na comunidade.",
    icon: "i-lucide-star",
  },
  {
    title: "Envio de comprovativos",
    description:
      "Sistema de envio e gerenciamento de comprovativos de pagamento e serviços.",
    icon: "i-lucide-credit-card",
  },
]);

const testimonials = computed(() => [
  {
    quote:
      "A plataforma mudou completamente a forma como encontro freelancers. Rápido, simples e confiável.",
    author: "Ana Souza",
    role: "CEO, Startup XYZ",
    avatar: "https://i.pravatar.cc/150?img=1",
  },
  {
    quote:
      "Consegui meu melhor projeto através daqui. A qualidade dos clientes é impressionante.",
    author: "Carlos Lima",
    role: "Designer Freelancer",
    avatar: "https://i.pravatar.cc/150?img=3",
  },
  {
    quote:
      "Interface incrível e suporte excelente. Recomendo para qualquer empresa que precise de talento.",
    author: "Mariana Costa",
    role: "CTO, Agência Digital",
    avatar: "https://i.pravatar.cc/150?img=5",
  },
  {
    quote:
      "Em menos de 24h já tinha propostas de qualidade. Nunca foi tão fácil contratar.",
    author: "Pedro Alves",
    role: "Empresário",
    avatar: "https://i.pravatar.cc/150?img=7",
  },
]);
</script>

<template>
  <div>
    <section class="px-8 py-6 bg-slate-900">
      <UPageCTA
        title="Conectando Jovens talentos com sonhos"
        description="Conectamos empresas e profissionais talentosos em Angola."
        variant="naked"
        color="primary"
        orientation="horizontal"
        :links="links"
      >
        <img src="~/assets/img/social.svg" class="w-full h-full object-cover" />
      </UPageCTA>
    </section>
    <section class="px-24 bg-blue-950 py-20 space-y-10 flex space-x-10">
      <div class="w-2/5">
        <img src="~/assets/img/work-time.svg" class="h-full" alt="app" />
      </div>
      <div class="w-3/5 space-y-6 flex flex-col">
        <AppUiHeaderFeatGroup
          title="Categorias Populares"
          description="Explore as categorias mais populares"
        />
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mt-6">
          <UPageCard
            v-for="card in cards"
            variant="ghost"
            :key="card.title"
            :title="card.title"
            :description="card.description"
            :icon="card.icon"
            :to="card.to"
            class="text-justify"
          />
        </div>
      </div>
    </section>
    <section class="px-24 py-20 space-y-10 flex space-x-10">
      <div class="w-3/5 space-y-6 flex flex-col">
        <AppUiHeaderFeatGroup
          title="Funcionalidades"
          description="Explore as funcionalidades da plataforma"
        />
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mt-6">
          <UPageCard
            v-for="feat in feats"
            variant="ghost"
            :key="feat.title"
            :title="feat.title"
            :description="feat.description"
            :icon="feat.icon"
            to="#"
            class="text-justify"
          />
        </div>
      </div>
      <div class="w-2/5">
        <img
          src="~/assets/img/dev.svg"
          class="h-full w-full bg-cover"
          alt="app"
        />
      </div>
    </section>
    <section class="px-24 flex bg-blue-950 py-30 space-x-10">
      <div class="w-1/3">
        <img
          src="~/assets/img/search.svg"
          alt="search"
          class="h-full w-full object-cover"
        />
      </div>
      <div class="w-2/3 space-y-6 flex flex-col">
        <AppUiHeaderFeatGroup
          title="Junte-se a nós"
          description="Faça parte da comunidade de freelancers"
        />

        <UPageCard
          title="Comece agora, e garanta a proposta"
          icon="i-lucide-rocket"
          variant="ghost"
          class="text-justify"
          description="A Bom de Freela permite que freelancers enviem propostas rápidas e profissionais, facilitando a escolha do melhor talento para cada projeto. A plataforma valoriza a qualidade, a confiança e a agilidade, conectando clientes a soluções eficientes e impulsionando oportunidades no mercado digital angolano."
        />
      </div>
    </section>
  </div>
</template>
