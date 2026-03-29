<script lang="ts" setup>
definePageMeta({ layout: "admin" });
useHead({ title: "Propostas — Admin | Bom de Freela" });

const search = ref("");
const filterStatus = ref("all");

const proposals = [
  { id: "1", freelancer: "Ana Ferreira", email: "ana.ferreira@email.com", project: "Desenvolvimento de App Mobile de Delivery", amount: "KZ 380.000", status: "accepted", submittedAt: "26 Mar 2026" },
  { id: "2", freelancer: "Marta Sousa", email: "marta.sousa@gmail.com", project: "Sistema de Gestão ERP para PME", amount: "KZ 1.100.000", status: "pending", submittedAt: "27 Mar 2026" },
  { id: "3", freelancer: "André Costa", email: "andre.costa@dev.ao", project: "Desenvolvimento de App Mobile de Delivery", amount: "KZ 420.000", status: "pending", submittedAt: "27 Mar 2026" },
  { id: "4", freelancer: "Beatriz Silva", email: "beatriz@gmail.com", project: "Redesign de Website Institucional", amount: "KZ 160.000", status: "rejected", submittedAt: "11 Mar 2026" },
  { id: "5", freelancer: "Sofia Lima", email: "sofia.lima@outlook.com", project: "Redação de Conteúdo para Blog Corporativo", amount: "KZ 40.000", status: "accepted", submittedAt: "06 Mar 2026" },
  { id: "6", freelancer: "Rui Baptista", email: "rbaptista@hotmail.com", project: "Consultoria em Segurança de TI", amount: "KZ 330.000", status: "pending", submittedAt: "19 Mar 2026" },
  { id: "7", freelancer: "Miguel Lopes", email: "mlopes@gmail.com", project: "Campanha de Marketing nas Redes Sociais", amount: "KZ 75.000", status: "pending", submittedAt: "21 Mar 2026" },
  { id: "8", freelancer: "Ana Ferreira", email: "ana.ferreira@email.com", project: "API REST para Plataforma E-Commerce", amount: "KZ 260.000", status: "accepted", submittedAt: "28 Mar 2026" },
  { id: "9", freelancer: "Marta Sousa", email: "marta.sousa@gmail.com", project: "Campanha de Marketing nas Redes Sociais", amount: "KZ 88.000", status: "rejected", submittedAt: "22 Mar 2026" },
];

const statusOptions = [
  { label: "Todos os status", value: "all" },
  { label: "Pendente", value: "pending" },
  { label: "Aceite", value: "accepted" },
  { label: "Rejeitada", value: "rejected" },
];

const statusConfig: Record<string, { color: "warning" | "success" | "error"; label: string }> = {
  pending: { color: "warning", label: "Pendente" },
  accepted: { color: "success", label: "Aceite" },
  rejected: { color: "error", label: "Rejeitada" },
};

const filtered = computed(() =>
  proposals.filter((p) => {
    const matchSearch =
      !search.value ||
      p.freelancer.toLowerCase().includes(search.value.toLowerCase()) ||
      p.project.toLowerCase().includes(search.value.toLowerCase());
    const matchStatus = filterStatus.value === "all" || p.status === filterStatus.value;
    return matchSearch && matchStatus;
  })
);

const columns = [
  { accessorKey: "freelancer", header: "Freelancer" },
  { accessorKey: "project", header: "Projeto" },
  { accessorKey: "amount", header: "Valor Proposto" },
  { accessorKey: "status", header: "Status" },
  { accessorKey: "submittedAt", header: "Enviada em" },
  { id: "actions", header: "" },
];

const countByStatus = (s: string) => proposals.filter((p) => p.status === s).length;
</script>

<template>
  <div class="space-y-6">
    <div>
      <h1 class="text-2xl font-bold text-white">Gerenciamento de Propostas</h1>
      <p class="text-slate-400 text-sm mt-1">Monitorar todas as propostas submetidas na plataforma</p>
    </div>

    <!-- Stats -->
    <div class="grid grid-cols-3 gap-4">
      <UCard class="border border-amber-500/20 bg-amber-500/5">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-2xl font-bold text-amber-400">{{ countByStatus("pending") }}</p>
            <p class="text-xs text-slate-400 mt-0.5">Pendentes</p>
          </div>
          <div class="h-10 w-10 rounded-xl bg-amber-500/10 flex items-center justify-center">
            <Icon name="i-lucide-clock" class="text-amber-400 text-lg" />
          </div>
        </div>
      </UCard>
      <UCard class="border border-emerald-500/20 bg-emerald-500/5">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-2xl font-bold text-emerald-400">{{ countByStatus("accepted") }}</p>
            <p class="text-xs text-slate-400 mt-0.5">Aceites</p>
          </div>
          <div class="h-10 w-10 rounded-xl bg-emerald-500/10 flex items-center justify-center">
            <Icon name="i-lucide-check-circle" class="text-emerald-400 text-lg" />
          </div>
        </div>
      </UCard>
      <UCard class="border border-rose-500/20 bg-rose-500/5">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-2xl font-bold text-rose-400">{{ countByStatus("rejected") }}</p>
            <p class="text-xs text-slate-400 mt-0.5">Rejeitadas</p>
          </div>
          <div class="h-10 w-10 rounded-xl bg-rose-500/10 flex items-center justify-center">
            <Icon name="i-lucide-x-circle" class="text-rose-400 text-lg" />
          </div>
        </div>
      </UCard>
    </div>

    <!-- Filters -->
    <UCard class="border border-slate-800">
      <div class="flex flex-col sm:flex-row gap-3">
        <UInput v-model="search" placeholder="Pesquisar por freelancer ou projeto..." icon="i-lucide-search" class="flex-1" />
        <USelect v-model="filterStatus" :items="statusOptions" value-key="value" label-key="label" class="w-48" />
      </div>
    </UCard>

    <!-- Table -->
    <UCard class="border border-slate-800">
      <template #header>
        <p class="text-sm text-slate-400">
          <span class="font-semibold text-white">{{ filtered.length }}</span> proposta(s) encontrada(s)
        </p>
      </template>

      <UTable :data="filtered" :columns="columns">
        <template #freelancer-cell="{ row }">
          <div class="flex items-center gap-3">
            <div class="h-8 w-8 rounded-full bg-violet-600 flex items-center justify-center text-xs font-bold text-white shrink-0">
              {{ row.original.freelancer.charAt(0) }}
            </div>
            <div>
              <p class="font-medium text-white text-sm">{{ row.original.freelancer }}</p>
              <p class="text-xs text-slate-500">{{ row.original.email }}</p>
            </div>
          </div>
        </template>

        <template #project-cell="{ row }">
          <p class="text-sm text-slate-300 max-w-xs leading-snug">{{ row.original.project }}</p>
        </template>

        <template #amount-cell="{ row }">
          <span class="font-semibold text-white text-sm">{{ row.original.amount }}</span>
        </template>

        <template #status-cell="{ row }">
          <UBadge :color="statusConfig[row.original.status].color" variant="subtle" size="sm">
            {{ statusConfig[row.original.status].label }}
          </UBadge>
        </template>

        <template #submittedAt-cell="{ row }">
          <span class="text-sm text-slate-400">{{ row.original.submittedAt }}</span>
        </template>

        <template #actions-cell="{ row }">
          <div class="flex items-center justify-end gap-1.5">
            <UButton size="xs" color="neutral" variant="ghost" icon="i-lucide-eye" label="Ver" />
            <UButton v-if="row.original.status !== 'rejected'" size="xs" color="error" variant="ghost" icon="i-lucide-flag" label="Sinalizar" />
          </div>
        </template>
      </UTable>
    </UCard>
  </div>
</template>
