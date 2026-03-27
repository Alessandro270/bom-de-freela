<script lang="ts" setup>
definePageMeta({ layout: "app" });

const proposals = [
  { id: 1, name: "Marcos Silva", sentAt: "23/03/2026", value: "320,000.00 KZ", status: null },
  { id: 2, name: "Ana Ferreira", sentAt: "23/03/2026", value: "410,000.00 KZ", status: null },
  { id: 3, name: "João Baptista", sentAt: "24/03/2026", value: "500,000.00 KZ", status: null },
];

const categories = ref([
  "Suporte Administrativo", "Design & Criatividade", "Marketing Digital",
  "Redação & Tradução", "Desenvolvimento", "Consultoria", "Multimédia",
]);
const category = ref("Desenvolvimento");
const subcategories: Record<string, string[]> = {
  "Suporte Administrativo": ["Entrada de Dados", "Gestão de Agenda", "Atendimento ao Cliente", "Pesquisa na Internet", "Assistente Virtual", "Organização de Documentos"],
  "Design & Criatividade": ["Design Gráfico", "UI/UX Design", "Criação de Logotipos", "Identidade Visual", "Design de Redes Sociais", "Ilustração"],
  "Marketing Digital": ["Gestão de Redes Sociais", "SEO (Otimização para Motores de Busca)", "Publicidade Online (Ads)", "Email Marketing", "Marketing de Conteúdo", "Análise de Métricas"],
  "Redação & Tradução": ["Redação de Artigos", "Copywriting", "Tradução de Documentos", "Revisão de Texto", "Criação de Conteúdo", "Legendagem"],
  Desenvolvimento: ["Desenvolvimento Web Frontend", "Desenvolvimento Web Backend", "Desenvolvimento Fullstack", "Desenvolvimento Mobile", "Criação de APIs", "Manutenção de Sistemas", "Integração de Sistemas"],
  Consultoria: ["Consultoria em Negócios", "Consultoria Financeira", "Consultoria em TI", "Planejamento Estratégico", "Gestão de Projetos", "Análise de Processos"],
  Multimédia: ["Edição de Vídeo", "Produção de Vídeo", "Animação 2D", "Animação 3D", "Produção de Áudio", "Fotografia"],
};
const currentSubcategory = computed(() => subcategories[category.value] || []);
const subcategory = ref(currentSubcategory.value[0] || "");
watch(category, () => { subcategory.value = currentSubcategory.value[0] || ""; });
const tags = ref<string[]>(["python", "javascript", "java"]);
</script>

<template>
  <AppLayoutWrapper>
    <div class="space-y-6">
      <!-- Cabeçalho da proposta -->
      <UCard>
        <div class="space-y-3">
          <div class="flex items-start justify-between gap-4">
            <h1 class="text-lg font-bold text-gray-900 dark:text-white leading-snug">
              Lorem ipsum, dolor sit amet consectetur adipisicing elit. Illo at,
              ratione totam fugiat omnis nobis iste placeat.
            </h1>
            <span class="text-lg font-bold text-violet-600 dark:text-violet-400 shrink-0">
              500,000.00 kz
            </span>
          </div>

          <div class="flex items-center gap-3 flex-wrap">
            <UiRating :value="5" />
            <span class="text-xs text-gray-400 dark:text-gray-500">
              Avaliações: <span class="font-medium text-gray-600 dark:text-gray-300">(5)</span>
            </span>
            <span class="text-xs text-gray-400 dark:text-gray-500">
              Postado em: <span class="font-medium text-gray-600 dark:text-gray-300">23/03/2026</span>
            </span>
          </div>
        </div>
      </UCard>

      <!-- Descrição + detalhes -->
      <UCard>
        <template #header>
          <div class="flex items-center justify-between">
            <div class="flex items-center gap-2">
              <UIcon name="i-lucide-file-text" class="h-4 w-4 text-gray-500" />
              <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">Descrição</span>
            </div>
            <!-- Modal editar proposta -->
            <UModal>
              <UButton size="xs" color="neutral" variant="ghost" icon="i-lucide-pencil" label="Editar" />
              <template #header>
                <div class="flex items-center gap-2">
                  <UIcon name="i-lucide-file-text" class="h-4 w-4 text-gray-500" />
                  <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">Editar proposta</span>
                </div>
              </template>
              <template #body>
                <UForm class="space-y-4">
                  <UFormField label="Título" name="title">
                    <UInput class="w-full" placeholder="Nova proposta" />
                  </UFormField>
                  <UFormField label="Descrição" name="description">
                    <UTextarea class="w-full" placeholder="Descrição da proposta" />
                  </UFormField>
                  <UFormField label="Preço inicial" name="startPrice">
                    <UInputNumber class="w-full" orientation="vertical" placeholder="350,000.00 kz" />
                  </UFormField>
                  <UFormField label="Categoria" name="category">
                    <USelectMenu class="w-full" v-model="category" :items="categories" />
                  </UFormField>
                  <UFormField label="Subcategoria" name="subcategory">
                    <USelectMenu class="w-full" v-model="subcategory" :items="currentSubcategory" />
                  </UFormField>
                  <UFormField label="Habilidades" name="skills">
                    <UInputTags class="w-full" v-model="tags" placeholder="vue, pinia.." />
                  </UFormField>
                  <UFormField label="Prazo" name="deadline">
                    <UInputDate class="w-full" />
                  </UFormField>
                </UForm>
              </template>
              <template #footer>
                <div class="flex items-center justify-between w-full">
                  <UButton color="error" variant="ghost" icon="i-lucide-trash-2" label="Eliminar" />
                  <UButton type="submit" color="primary" variant="solid" icon="i-lucide-save" label="Salvar" />
                </div>
              </template>
            </UModal>
          </div>
        </template>

        <div class="space-y-4">
          <p class="text-sm text-gray-600 dark:text-gray-400 leading-relaxed text-justify">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
            ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
            voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
            ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
            voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
          </p>

          <USeparator />

          <div class="grid grid-cols-1 sm:grid-cols-3 gap-3">
            <div>
              <p class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide">Categoria</p>
              <p class="text-sm font-medium text-gray-900 dark:text-white mt-0.5">Desenvolvimento de Software</p>
            </div>
            <div>
              <p class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide">Subcategoria</p>
              <p class="text-sm font-medium text-gray-900 dark:text-white mt-0.5">Desenvolvimento Web</p>
            </div>
            <div>
              <p class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide">Prazo</p>
              <p class="text-sm font-medium text-gray-900 dark:text-white mt-0.5">30/03/2026</p>
            </div>
          </div>

          <div>
            <p class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide mb-2">
              Habilidades necessárias
            </p>
            <div class="flex gap-2 flex-wrap">
              <UBadge v-for="tag in tags" :key="tag" color="primary" variant="subtle" size="sm">
                {{ tag }}
              </UBadge>
            </div>
          </div>
        </div>
      </UCard>

      <!-- Propostas dos freelancers -->
      <div>
        <div class="flex items-center gap-2 mb-3">
          <h2 class="text-sm font-semibold text-gray-700 dark:text-gray-300 uppercase tracking-wide">
            Propostas recebidas
          </h2>
          <UBadge color="neutral" variant="subtle" size="xs">{{ proposals.length }}</UBadge>
        </div>
        <div class="grid gap-4 grid-cols-1 sm:grid-cols-2">
          <AppUiCardFreelancerProposal
            v-for="proposal in proposals"
            :key="proposal.id"
            :name="proposal.name"
            :sent-at="proposal.sentAt"
            :value="proposal.value"
          >
            Lorem ipsum dolor sit amet consectetur, adipisicing elit. Eveniet ut
            ullam, et optio enim qui porro commodi minima reprehenderit nam.
          </AppUiCardFreelancerProposal>
        </div>
      </div>
    </div>
  </AppLayoutWrapper>
</template>
