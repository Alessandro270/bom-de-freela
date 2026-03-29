<script lang="ts" setup>
definePageMeta({ layout: "admin" });
useHead({ title: "Clientes — Admin | Bom de Freela" });

const search = ref("");
const filterStatus = ref("all");

const clients = [
  { id: "1", name: "Carlos Neto", email: "cneto@empresa.ao", company: "Empresa Luanda Lda.", projects: 5, totalSpent: "KZ 320.000", status: "active", memberSince: "Jan 2026" },
  { id: "2", name: "Pedro Alves", email: "palves@tech.ao", company: "Tech Angola", projects: 8, totalSpent: "KZ 680.000", status: "active", memberSince: "Nov 2025" },
  { id: "3", name: "João Martins", email: "jmartins@luanda.ao", company: "Martins & Associados", projects: 2, totalSpent: "KZ 90.000", status: "pending", memberSince: "Mar 2026" },
  { id: "4", name: "Laura Costa", email: "lcosta@agencia.ao", company: "Agência Digital AO", projects: 12, totalSpent: "KZ 1.200.000", status: "active", memberSince: "Jul 2025" },
  { id: "5", name: "Tecnologias Luanda", email: "info@tecnoluanda.ao", company: "Tecnologias Luanda S.A.", projects: 3, totalSpent: "KZ 450.000", status: "active", memberSince: "Feb 2026" },
  { id: "6", name: "Maria Santos", email: "maria.santos@startup.ao", company: "StartupAO", projects: 1, totalSpent: "KZ 35.000", status: "suspended", memberSince: "Mar 2026" },
];

const statusOptions = [
  { label: "Todos os status", value: "all" },
  { label: "Ativo", value: "active" },
  { label: "Pendente", value: "pending" },
  { label: "Suspenso", value: "suspended" },
];

const statusConfig: Record<string, { color: "success" | "warning" | "error"; label: string }> = {
  active: { color: "success", label: "Ativo" },
  pending: { color: "warning", label: "Pendente" },
  suspended: { color: "error", label: "Suspenso" },
};

const filtered = computed(() =>
  clients.filter((c) => {
    const matchSearch =
      !search.value ||
      c.name.toLowerCase().includes(search.value.toLowerCase()) ||
      c.company.toLowerCase().includes(search.value.toLowerCase());
    const matchStatus = filterStatus.value === "all" || c.status === filterStatus.value;
    return matchSearch && matchStatus;
  })
);

const columns = [
  { accessorKey: "name", header: "Cliente" },
  { accessorKey: "company", header: "Empresa" },
  { accessorKey: "projects", header: "Projetos" },
  { accessorKey: "totalSpent", header: "Total Gasto" },
  { accessorKey: "memberSince", header: "Membro desde" },
  { accessorKey: "status", header: "Status" },
  { id: "actions", header: "" },
];
</script>

<template>
  <div class="space-y-6">
    <div class="flex items-center justify-between">
      <div>
        <h1 class="text-2xl font-bold text-white">Gerenciamento de Clientes</h1>
        <p class="text-slate-400 text-sm mt-1">Gerir todos os perfis de clientes da plataforma</p>
      </div>
    </div>

    <!-- Stats -->
    <div class="grid grid-cols-3 gap-4">
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-white">{{ clients.length }}</p>
        <p class="text-xs text-slate-400 mt-0.5">Total de clientes</p>
      </UCard>
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-emerald-400">
          {{ clients.reduce((acc, c) => acc + c.projects, 0) }}
        </p>
        <p class="text-xs text-slate-400 mt-0.5">Projetos publicados</p>
      </UCard>
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-blue-400">
          {{ clients.filter((c) => c.status === "active").length }}
        </p>
        <p class="text-xs text-slate-400 mt-0.5">Contas ativas</p>
      </UCard>
    </div>

    <!-- Filters -->
    <UCard class="border border-slate-800">
      <div class="flex flex-col sm:flex-row gap-3">
        <UInput v-model="search" placeholder="Pesquisar por nome ou empresa..." icon="i-lucide-search" class="flex-1" />
        <USelect v-model="filterStatus" :items="statusOptions" value-key="value" label-key="label" class="w-48" />
      </div>
    </UCard>

    <!-- Table -->
    <UCard class="border border-slate-800">
      <template #header>
        <p class="text-sm text-slate-400">
          <span class="font-semibold text-white">{{ filtered.length }}</span> cliente(s) encontrado(s)
        </p>
      </template>

      <UTable :data="filtered" :columns="columns">
        <template #name-cell="{ row }">
          <div class="flex items-center gap-3">
            <div class="h-9 w-9 rounded-full bg-blue-600 flex items-center justify-center text-sm font-bold text-white shrink-0">
              {{ row.original.name.charAt(0) }}
            </div>
            <div>
              <p class="font-medium text-white text-sm">{{ row.original.name }}</p>
              <p class="text-xs text-slate-500">{{ row.original.email }}</p>
            </div>
          </div>
        </template>

        <template #company-cell="{ row }">
          <div class="flex items-center gap-1.5">
            <Icon name="i-lucide-building-2" class="text-slate-500 text-sm shrink-0" />
            <span class="text-sm text-slate-300">{{ row.original.company }}</span>
          </div>
        </template>

        <template #projects-cell="{ row }">
          <UBadge color="info" variant="subtle" size="sm">{{ row.original.projects }} projetos</UBadge>
        </template>

        <template #totalSpent-cell="{ row }">
          <span class="font-semibold text-white text-sm">{{ row.original.totalSpent }}</span>
        </template>

        <template #memberSince-cell="{ row }">
          <span class="text-sm text-slate-400">{{ row.original.memberSince }}</span>
        </template>

        <template #status-cell="{ row }">
          <UBadge :color="statusConfig[row.original.status].color" variant="subtle" size="sm">
            {{ statusConfig[row.original.status].label }}
          </UBadge>
        </template>

        <template #actions-cell="{ row }">
          <div class="flex items-center justify-end gap-1.5">
            <UButton size="xs" color="neutral" variant="ghost" icon="i-lucide-eye" label="Ver" />
            <UButton v-if="row.original.status === 'active'" size="xs" color="error" variant="subtle" icon="i-lucide-shield-off" label="Suspender" />
            <UButton v-if="row.original.status !== 'active'" size="xs" color="success" variant="subtle" icon="i-lucide-shield-check" label="Ativar" />
          </div>
        </template>
      </UTable>
    </UCard>
  </div>
</template>
