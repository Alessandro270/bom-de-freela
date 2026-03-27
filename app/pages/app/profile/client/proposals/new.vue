<script lang="ts" setup>
definePageMeta({ layout: "app" });

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
const tags = ref<string[]>([]);
</script>

<template>
  <AppLayoutWrapper>
    <UCard>
      <template #header>
        <div class="flex items-center gap-2">
          <UIcon name="i-lucide-plus-circle" class="h-4 w-4 text-gray-500" />
          <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">
            Nova proposta
          </span>
        </div>
      </template>

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
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
          <UFormField label="Categoria" name="category">
            <USelectMenu class="w-full" v-model="category" :items="categories" />
          </UFormField>
          <UFormField label="Subcategoria" name="subcategory">
            <USelectMenu class="w-full" v-model="subcategory" :items="currentSubcategory" />
          </UFormField>
        </div>
        <UFormField label="Habilidades" name="skills">
          <UInputTags class="w-full" v-model="tags" placeholder="vue, pinia.." />
        </UFormField>
        <UFormField label="Prazo" name="deadline">
          <UInputDate class="w-full" />
        </UFormField>

        <div class="flex justify-end pt-2">
          <UButton
            type="submit"
            color="primary"
            variant="solid"
            icon="i-lucide-send"
            label="Postar proposta"
          />
        </div>
      </UForm>
    </UCard>
  </AppLayoutWrapper>
</template>
