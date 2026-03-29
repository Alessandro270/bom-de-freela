<script lang="ts" setup>
definePageMeta({ layout: "admin" });
useHead({ title: "Gerenciamento de Contas — Admin | Bom de Freela" });

const search = ref("");
const filterType = ref("all");
const filterStatus = ref("all");

const accounts = [
  { id: "1", name: "Ana Ferreira", email: "ana.ferreira@email.com", type: "freelancer", status: "active", joinedAt: "12 Jan 2026" },
  { id: "2", name: "Carlos Neto", email: "cneto@empresa.ao", type: "client", status: "active", joinedAt: "05 Fev 2026" },
  { id: "3", name: "Beatriz Silva", email: "beatriz@gmail.com", type: "freelancer", status: "suspended", joinedAt: "20 Fev 2026" },
  { id: "4", name: "João Martins", email: "jmartins@luanda.ao", type: "client", status: "pending", joinedAt: "02 Mar 2026" },
  { id: "5", name: "Sofia Lima", email: "sofia.lima@outlook.com", type: "freelancer", status: "active", joinedAt: "10 Mar 2026" },
  { id: "6", name: "Pedro Alves", email: "palves@tech.ao", type: "client", status: "active", joinedAt: "15 Mar 2026" },
  { id: "7", name: "Miguel Lopes", email: "mlopes@gmail.com", type: "freelancer", status: "pending", joinedAt: "18 Mar 2026" },
  { id: "8", name: "Laura Costa", email: "lcosta@agencia.ao", type: "client", status: "active", joinedAt: "22 Mar 2026" },
  { id: "9", name: "Rui Baptista", email: "rbaptista@hotmail.com", type: "freelancer", status: "suspended", joinedAt: "25 Mar 2026" },
  { id: "10", name: "Marta Sousa", email: "marta.sousa@gmail.com", type: "freelancer", status: "active", joinedAt: "27 Mar 2026" },
];

const typeOptions = [
  { label: "Todos os tipos", value: "all" },
  { label: "Freelancer", value: "freelancer" },
  { label: "Cliente", value: "client" },
];

const statusOptions = [
  { label: "Todos os status", value: "all" },
  { label: "Ativo", value: "active" },
  { label: "Pendente", value: "pending" },
  { label: "Suspenso", value: "suspended" },
];

const filtered = computed(() =>
  accounts.filter((a) => {
    const matchSearch =
      !search.value ||
      a.name.toLowerCase().includes(search.value.toLowerCase()) ||
      a.email.toLowerCase().includes(search.value.toLowerCase());
    const matchType = filterType.value === "all" || a.type === filterType.value;
    const matchStatus = filterStatus.value === "all" || a.status === filterStatus.value;
    return matchSearch && matchType && matchStatus;
  })
);

const columns = [
  { accessorKey: "name", header: "Utilizador" },
  { accessorKey: "type", header: "Tipo" },
  { accessorKey: "status", header: "Status" },
  { accessorKey: "joinedAt", header: "Cadastrado em" },
  { id: "actions", header: "" },
];

const statusConfig: Record<string, { color: "success" | "warning" | "error"; label: string }> = {
  active: { color: "success", label: "Ativo" },
  pending: { color: "warning", label: "Pendente" },
  suspended: { color: "error", label: "Suspenso" },
};
</script>

<template>
  <div class="space-y-6">
    <div class="flex items-center justify-between">
      <div>
        <h1 class="text-2xl font-bold text-white">Gerenciamento de Contas</h1>
        <p class="text-slate-400 text-sm mt-1">Gerir todas as contas da plataforma</p>
      </div>
      <UButton icon="i-lucide-user-plus" label="Nova Conta" color="primary" />
    </div>

    <!-- Stats -->
    <div class="grid grid-cols-3 gap-4">
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-white">{{ accounts.length }}</p>
        <p class="text-xs text-slate-400 mt-0.5">Total de contas</p>
      </UCard>
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-amber-400">
          {{ accounts.filter((a) => a.status === "pending").length }}
        </p>
        <p class="text-xs text-slate-400 mt-0.5">Pendentes</p>
      </UCard>
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-rose-400">
          {{ accounts.filter((a) => a.status === "suspended").length }}
        </p>
        <p class="text-xs text-slate-400 mt-0.5">Suspensas</p>
      </UCard>
    </div>

    <!-- Filters -->
    <UCard class="border border-slate-800">
      <div class="flex flex-col sm:flex-row gap-3">
        <UInput v-model="search" placeholder="Pesquisar por nome ou email..." icon="i-lucide-search" class="flex-1" />
        <USelect v-model="filterType" :items="typeOptions" value-key="value" label-key="label" class="w-48" />
        <USelect v-model="filterStatus" :items="statusOptions" value-key="value" label-key="label" class="w-48" />
      </div>
    </UCard>

    <!-- Table -->
    <UCard class="border border-slate-800">
      <template #header>
        <p class="text-sm text-slate-400">
          <span class="font-semibold text-white">{{ filtered.length }}</span> conta(s) encontrada(s)
        </p>
      </template>

      <UTable :data="filtered" :columns="columns">
        <template #name-cell="{ row }">
          <div class="flex items-center gap-3">
            <div class="h-9 w-9 rounded-full bg-slate-700 flex items-center justify-center text-sm font-bold text-white shrink-0">
              {{ row.original.name.charAt(0) }}
            </div>
            <div>
              <p class="font-medium text-white text-sm">{{ row.original.name }}</p>
              <p class="text-xs text-slate-500">{{ row.original.email }}</p>
            </div>
          </div>
        </template>

        <template #type-cell="{ row }">
          <UBadge :color="row.original.type === 'freelancer' ? 'secondary' : 'info'" variant="subtle" size="sm">
            <Icon :name="row.original.type === 'freelancer' ? 'i-lucide-user-check' : 'i-lucide-building-2'" class="mr-1 text-xs" />
            {{ row.original.type === "freelancer" ? "Freelancer" : "Cliente" }}
          </UBadge>
        </template>

        <template #status-cell="{ row }">
          <UBadge :color="statusConfig[row.original.status].color" variant="subtle" size="sm">
            {{ statusConfig[row.original.status].label }}
          </UBadge>
        </template>

        <template #joinedAt-cell="{ row }">
          <span class="text-sm text-slate-400">{{ row.original.joinedAt }}</span>
        </template>

        <template #actions-cell="{ row }">
          <div class="flex items-center justify-end gap-1.5">
            <UButton size="xs" color="neutral" variant="ghost" icon="i-lucide-eye" label="Ver" />
            <UButton v-if="row.original.status === 'pending'" size="xs" color="success" variant="subtle" icon="i-lucide-check" label="Ativar" />
            <UButton v-if="row.original.status === 'active'" size="xs" color="error" variant="subtle" icon="i-lucide-shield-off" label="Suspender" />
            <UButton v-if="row.original.status === 'suspended'" size="xs" color="warning" variant="subtle" icon="i-lucide-shield-check" label="Reativar" />
          </div>
        </template>
      </UTable>
    </UCard>
  </div>
</template>
