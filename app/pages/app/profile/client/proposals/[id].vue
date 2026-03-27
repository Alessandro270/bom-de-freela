<script lang="ts" setup>
definePageMeta({ layout: "app" });

const proposals = [
  {
    id: 1,
    name: "Marcos Silva",
    sentAt: "23/03/2026",
    value: "320,000.00 KZ",
    status: null,
  },
  {
    id: 2,
    name: "Ana Ferreira",
    sentAt: "23/03/2026",
    value: "410,000.00 KZ",
    status: null,
  },
  {
    id: 3,
    name: "João Baptista",
    sentAt: "24/03/2026",
    value: "500,000.00 KZ",
    status: null,
  },
];
const categories = ref([
  "Suporte Administrativo",
  "Design & Criatividade",
  "Marketing Digital",
  "Redação & Tradução",
  "Desenvolvimento",
  "Consultoria",
  "Multimédia",
]);
const category = ref("Desenvolvimento");
const subcategories: Record<string, string[]> = {
  "Suporte Administrativo": [
    "Entrada de Dados",
    "Gestão de Agenda",
    "Atendimento ao Cliente",
    "Pesquisa na Internet",
    "Assistente Virtual",
    "Organização de Documentos",
  ],

  "Design & Criatividade": [
    "Design Gráfico",
    "UI/UX Design",
    "Criação de Logotipos",
    "Identidade Visual",
    "Design de Redes Sociais",
    "Ilustração",
  ],

  "Marketing Digital": [
    "Gestão de Redes Sociais",
    "SEO (Otimização para Motores de Busca)",
    "Publicidade Online (Ads)",
    "Email Marketing",
    "Marketing de Conteúdo",
    "Análise de Métricas",
  ],

  "Redação & Tradução": [
    "Redação de Artigos",
    "Copywriting",
    "Tradução de Documentos",
    "Revisão de Texto",
    "Criação de Conteúdo",
    "Legendagem",
  ],

  Desenvolvimento: [
    "Desenvolvimento Web Frontend",
    "Desenvolvimento Web Backend",
    "Desenvolvimento Fullstack",
    "Desenvolvimento Mobile",
    "Criação de APIs",
    "Manutenção de Sistemas",
    "Integração de Sistemas",
  ],

  Consultoria: [
    "Consultoria em Negócios",
    "Consultoria Financeira",
    "Consultoria em TI",
    "Planejamento Estratégico",
    "Gestão de Projetos",
    "Análise de Processos",
  ],

  Multimédia: [
    "Edição de Vídeo",
    "Produção de Vídeo",
    "Animação 2D",
    "Animação 3D",
    "Produção de Áudio",
    "Fotografia",
  ],
};
const currentSubcategory = computed(() => subcategories[category.value] || []);
const subcategory = ref(currentSubcategory.value[0] || "");

watch(category, () => {
  subcategory.value = currentSubcategory.value[0] || "";
});
const tags = ref([]);

const statuses = ref<Record<number, "accepted" | "rejected" | null>>(
  Object.fromEntries(proposals.map((p) => [p.id, p.status])),
);
</script>

<template>
  <div
    class="font-google justify-center flex flex-col space-y-10 max-w-2/3 mx-auto"
  >
    <div class="w-full">
      <div class="space-y-2">
        <h1 class="text-2xl font-medium text-justify">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat.
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
        <div class="flex items-end justify-between">
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
          <UModal>
            <UButton label="Editar" color="neutral" variant="subtle" />
            <template #title>
              <AppUiHeaderProfile>Editar proposta</AppUiHeaderProfile>
            </template>
            <template #body>
              <UForm class="flex flex-col space-y-4">
                <UFormField label="Titulo" name="title">
                  <UInput class="w-full" placeholder="Nova proposta" />
                </UFormField>
                <UFormField label="Descrição" name="description">
                  <UTextarea
                    class="w-full"
                    placeholder="Descricao da proposta"
                  />
                </UFormField>
                <UFormField label="Preço inicial" name="startPrice">
                  <UInputNumber
                    class="w-full"
                    orientation="vertical"
                    placeholder="350,000.00 kz"
                  />
                </UFormField>
                <UFormField label="Categoria" name="category">
                  <USelectMenu
                    class="w-full"
                    v-model="category"
                    :items="categories"
                  />
                </UFormField>
                <UFormField label="Subcategoria" name="Subcategory">
                  <USelectMenu
                    class="w-full"
                    v-model="subcategory"
                    :items="currentSubcategory"
                  />
                </UFormField>
                <UFormField label="Habilidades" name="skills">
                  <UInputTags
                    class="w-full"
                    v-model="tags"
                    placeholder="vue, pinia.."
                  />
                </UFormField>
                <UFormField label="prazo" name="skills">
                  <UInputDate class="w-full" />
                </UFormField>
              </UForm>
            </template>
            <template #footer>
              <div class="flex w-full space-x-3 justify-end">
                <UModal>
                  <AppUiButtonSideSecondary>Eliminar</AppUiButtonSideSecondary>
                  <template #content>
                    <AppUiCardConfirm />
                  </template>
                </UModal>
                <AppUiButtonSidePrimary type="submit">
                  Salvar
                </AppUiButtonSidePrimary>
              </div>
            </template>
          </UModal>
        </div>
      </div>
    </div>
    <div class="grid gap-6 grid-cols-2">
      <AppUiCardFreelancerProposal
        v-for="proposal in proposals"
        :key="proposal.id"
        :name="proposal.name"
        :sent-at="proposal.sentAt"
        :value="proposal.value"
      >
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Eveniet ut
        ullam, et optio enim qui porro commodi minima reprehenderit nam corrupti
        officia. Repellat, rem nulla. Veniam ex error quasi. Ipsam.
      </AppUiCardFreelancerProposal>
    </div>
  </div>
</template>
