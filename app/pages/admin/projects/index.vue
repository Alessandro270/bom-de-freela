<script lang="ts" setup>
definePageMeta({ layout: "admin" });
useHead({ title: "Projetos — Admin | Bom de Freela" });

const search = ref("");
const filterStatus = ref("all");
const filterCategory = ref("all");

const projects = [
  { id: "1", title: "Desenvolvimento de App Mobile de Delivery", client: "Carlos Neto", category: "Desenvolvimento", budget: "KZ 450.000", status: "active", proposals: 7, publishedAt: "25 Mar 2026" },
  { id: "2", title: "Sistema de Gestão ERP para PME", client: "Laura Costa", category: "Desenvolvimento", budget: "KZ 1.200.000", status: "active", proposals: 4, publishedAt: "22 Mar 2026" },
  { id: "3", title: "Redesign de Website Institucional", client: "Pedro Alves", category: "Design", budget: "KZ 180.000", status: "completed", proposals: 12, publishedAt: "10 Mar 2026" },
  { id: "4", title: "Campanha de Marketing nas Redes Sociais", client: "Tecnologias Luanda", category: "Marketing", budget: "KZ 90.000", status: "active", proposals: 9, publishedAt: "20 Mar 2026" },
  { id: "5", title: "Redação de Conteúdo para Blog Corporativo", client: "Laura Costa", category: "Redação", budget: "KZ 45.000", status: "completed", proposals: 6, publishedAt: "05 Mar 2026" },
  { id: "6", title: "Consultoria em Segurança de TI", client: "Pedro Alves", category: "Consultoria", budget: "KZ 350.000", status: "paused", proposals: 2, publishedAt: "18 Mar 2026" },
  { id: "7", title: "Criação de Logótipo e Identidade Visual", client: "Maria Santos", category: "Design", budget: "KZ 60.000", status: "cancelled", proposals: 3, publishedAt: "01 Mar 2026" },
  { id: "8", title: "API REST para Plataforma E-Commerce", client: "Carlos Neto", category: "Desenvolvimento", budget: "KZ 280.000", status: "active", proposals: 5, publishedAt: "27 Mar 2026" },
];

const categories = ["Desenvolvimento", "Design", "Marketing", "Redação", "Consultoria"];

const categoryOptions = [
  { label: "Todas as categorias", value: "all" },
  ...categories.map((c) => ({ label: c, value: c })),
];

const statusOptions = [
  { label: "Todos os status", value: "all" },
  { label: "Ativo", value: "active" },
  { label: "Concluído", value: "completed" },
  { label: "Pausado", value: "paused" },
  { label: "Cancelado", value: "cancelled" },
];

const statusConfig: Record<string, { color: "success" | "info" | "warning" | "error"; label: string }> = {
  active: { color: "success", label: "Ativo" },
  completed: { color: "info", label: "Concluído" },
  paused: { color: "warning", label: "Pausado" },
  cancelled: { color: "error", label: "Cancelado" },
};

const categoryIcons: Record<string, string> = {
  Desenvolvimento: "i-lucide-code",
  Design: "i-lucide-palette",
  Marketing: "i-lucide-megaphone",
  Redação: "i-lucide-file-text",
  Consultoria: "i-lucide-lightbulb",
};

const filtered = computed(() =>
  projects.filter((p) => {
    const matchSearch =
      !search.value ||
      p.title.toLowerCase().includes(search.value.toLowerCase()) ||
      p.client.toLowerCase().includes(search.value.toLowerCase());
    const matchStatus = filterStatus.value === "all" || p.status === filterStatus.value;
    const matchCategory = filterCategory.value === "all" || p.category === filterCategory.value;
    return matchSearch && matchStatus && matchCategory;
  })
);

const columns = [
  { accessorKey: "title", header: "Projeto" },
  { accessorKey: "client", header: "Cliente" },
  { accessorKey: "category", header: "Categoria" },
  { accessorKey: "budget", header: "Orçamento" },
  { accessorKey: "proposals", header: "Propostas" },
  { accessorKey: "status", header: "Status" },
  { accessorKey: "publishedAt", header: "Publicado" },
  { id: "actions", header: "" },
];
</script>

<template>
  <div class="space-y-6">
    <div>
      <h1 class="text-2xl font-bold text-white">Gerenciamento de Projetos</h1>
      <p class="text-slate-400 text-sm mt-1">Monitorar e moderar todos os projetos publicados</p>
    </div>

    <!-- Stats -->
    <div class="grid grid-cols-4 gap-4">
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-white">{{ projects.length }}</p>
        <p class="text-xs text-slate-400 mt-0.5">Total</p>
      </UCard>
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-emerald-400">{{ projects.filter((p) => p.status === "active").length }}</p>
        <p class="text-xs text-slate-400 mt-0.5">Ativos</p>
      </UCard>
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-sky-400">{{ projects.filter((p) => p.status === "completed").length }}</p>
        <p class="text-xs text-slate-400 mt-0.5">Concluídos</p>
      </UCard>
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-slate-400">{{ projects.reduce((acc, p) => acc + p.proposals, 0) }}</p>
        <p class="text-xs text-slate-400 mt-0.5">Propostas enviadas</p>
      </UCard>
    </div>

    <!-- Filters -->
    <UCard class="border border-slate-800">
      <div class="flex flex-col sm:flex-row gap-3">
        <UInput v-model="search" placeholder="Pesquisar por título ou cliente..." icon="i-lucide-search" class="flex-1" />
        <USelect v-model="filterCategory" :items="categoryOptions" value-key="value" label-key="label" class="w-52" />
        <USelect v-model="filterStatus" :items="statusOptions" value-key="value" label-key="label" class="w-44" />
      </div>
    </UCard>

    <!-- Table -->
    <UCard class="border border-slate-800">
      <template #header>
        <p class="text-sm text-slate-400">
          <span class="font-semibold text-white">{{ filtered.length }}</span> projeto(s) encontrado(s)
        </p>
      </template>

      <UTable :data="filtered" :columns="columns">
        <template #title-cell="{ row }">
          <p class="font-medium text-white text-sm max-w-xs leading-snug">{{ row.original.title }}</p>
        </template>

        <template #client-cell="{ row }">
          <div class="flex items-center gap-2">
            <div class="h-7 w-7 rounded-full bg-blue-600 flex items-center justify-center text-xs font-bold text-white shrink-0">
              {{ row.original.client.charAt(0) }}
            </div>
            <span class="text-sm text-slate-300">{{ row.original.client }}</span>
          </div>
        </template>

        <template #category-cell="{ row }">
          <div class="flex items-center gap-1.5">
            <Icon :name="categoryIcons[row.original.category] ?? 'i-lucide-tag'" class="text-slate-400 text-sm" />
            <span class="text-sm text-slate-300">{{ row.original.category }}</span>
          </div>
        </template>

        <template #budget-cell="{ row }">
          <span class="font-semibold text-white text-sm">{{ row.original.budget }}</span>
        </template>

        <template #proposals-cell="{ row }">
          <UBadge color="neutral" variant="subtle" size="sm">
            {{ row.original.proposals }} proposta{{ row.original.proposals !== 1 ? "s" : "" }}
          </UBadge>
        </template>

        <template #status-cell="{ row }">
          <UBadge :color="statusConfig[row.original.status].color" variant="subtle" size="sm">
            {{ statusConfig[row.original.status].label }}
          </UBadge>
        </template>

        <template #publishedAt-cell="{ row }">
          <span class="text-sm text-slate-400">{{ row.original.publishedAt }}</span>
        </template>

        <template #actions-cell="{ row }">
          <div class="flex items-center justify-end gap-1.5">
            <UButton size="xs" color="neutral" variant="ghost" icon="i-lucide-eye" label="Ver" />
            <UButton v-if="row.original.status === 'active'" size="xs" color="warning" variant="subtle" icon="i-lucide-pause" label="Pausar" />
            <UButton v-if="row.original.status !== 'cancelled'" size="xs" color="error" variant="ghost" icon="i-lucide-ban" />
          </div>
        </template>
      </UTable>
    </UCard>
  </div>
</template>
