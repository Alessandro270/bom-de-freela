<script lang="ts" setup>
definePageMeta({ layout: "app" });
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
</script>

<template>
  <div class="max-w-5xl mx-auto px-6 rounded-sm py-7 bg-slate-950 space-y-4">
    <AppUiHeaderTitle>Nova proposta</AppUiHeaderTitle>
    <UForm class="flex flex-col space-y-4">
      <UFormField label="Titulo" name="title">
        <UInput class="w-full" placeholder="Nova proposta" />
      </UFormField>
      <UFormField label="Descrição" name="description">
        <UTextarea class="w-full" placeholder="Descricao da proposta" />
      </UFormField>
      <UFormField label="Preço inicial" name="startPrice">
        <UInputNumber
          class="w-full"
          orientation="vertical"
          placeholder="350,000.00 kz"
        />
      </UFormField>
      <UFormField label="Categoria" name="category">
        <USelectMenu class="w-full" v-model="category" :items="categories" />
      </UFormField>
      <UFormField label="Subcategoria" name="Subcategory">
        <USelectMenu
          class="w-full"
          v-model="subcategory"
          :items="currentSubcategory"
        />
      </UFormField>
      <UFormField label="Habilidades" name="skills">
        <UInputTags class="w-full" v-model="tags" placeholder="vue, pinia.." />
      </UFormField>
      <UFormField label="prazo" name="skills">
        <UInputDate class="w-full" />
      </UFormField>

      <AppUiButtonPrimary type="submit" to="#" class="mt-3">
        Postar
      </AppUiButtonPrimary>
    </UForm>
  </div>
</template>
