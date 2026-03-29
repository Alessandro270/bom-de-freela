<script lang="ts" setup>
definePageMeta({ layout: "admin" });
useHead({ title: "Freelancers — Admin | Bom de Freela" });

const search = ref("");
const filterStatus = ref("all");
const filterSpeciality = ref("all");

const freelancers = [
  { id: "1", name: "Ana Ferreira", email: "ana.ferreira@email.com", speciality: "Desenvolvimento Web", rating: 4.9, proposals: 18, profileStatus: "verified", accountStatus: "active", memberSince: "Jan 2026" },
  { id: "2", name: "Beatriz Silva", email: "beatriz@gmail.com", speciality: "Design UI/UX", rating: 4.7, proposals: 12, profileStatus: "verified", accountStatus: "suspended", memberSince: "Fev 2026" },
  { id: "3", name: "Miguel Lopes", email: "mlopes@gmail.com", speciality: "Marketing Digital", rating: 0, proposals: 0, profileStatus: "unverified", accountStatus: "pending", memberSince: "Mar 2026" },
  { id: "4", name: "Sofia Lima", email: "sofia.lima@outlook.com", speciality: "Redação & Conteúdo", rating: 4.5, proposals: 7, profileStatus: "verified", accountStatus: "active", memberSince: "Mar 2026" },
  { id: "5", name: "Rui Baptista", email: "rbaptista@hotmail.com", speciality: "Desenvolvimento Mobile", rating: 4.2, proposals: 22, profileStatus: "verified", accountStatus: "suspended", memberSince: "Dez 2025" },
  { id: "6", name: "Marta Sousa", email: "marta.sousa@gmail.com", speciality: "Consultoria TI", rating: 5.0, proposals: 31, profileStatus: "verified", accountStatus: "active", memberSince: "Out 2025" },
  { id: "7", name: "André Costa", email: "andre.costa@dev.ao", speciality: "Desenvolvimento Web", rating: 3.8, proposals: 5, profileStatus: "unverified", accountStatus: "active", memberSince: "Mar 2026" },
];

const specialities = ["Desenvolvimento Web", "Desenvolvimento Mobile", "Design UI/UX", "Marketing Digital", "Redação & Conteúdo", "Consultoria TI"];

const specialityOptions = [
  { label: "Todas as especialidades", value: "all" },
  ...specialities.map((s) => ({ label: s, value: s })),
];

const statusOptions = [
  { label: "Todos os status", value: "all" },
  { label: "Ativo", value: "active" },
  { label: "Pendente", value: "pending" },
  { label: "Suspenso", value: "suspended" },
];

const accountStatusConfig: Record<string, { color: "success" | "warning" | "error"; label: string }> = {
  active: { color: "success", label: "Ativo" },
  pending: { color: "warning", label: "Pendente" },
  suspended: { color: "error", label: "Suspenso" },
};

const specialityColors: Record<string, string> = {
  "Desenvolvimento Web": "text-blue-400 bg-blue-500/10",
  "Desenvolvimento Mobile": "text-purple-400 bg-purple-500/10",
  "Design UI/UX": "text-pink-400 bg-pink-500/10",
  "Marketing Digital": "text-amber-400 bg-amber-500/10",
  "Redação & Conteúdo": "text-emerald-400 bg-emerald-500/10",
  "Consultoria TI": "text-sky-400 bg-sky-500/10",
};

const filtered = computed(() =>
  freelancers.filter((f) => {
    const matchSearch =
      !search.value ||
      f.name.toLowerCase().includes(search.value.toLowerCase()) ||
      f.speciality.toLowerCase().includes(search.value.toLowerCase());
    const matchStatus = filterStatus.value === "all" || f.accountStatus === filterStatus.value;
    const matchSpec = filterSpeciality.value === "all" || f.speciality === filterSpeciality.value;
    return matchSearch && matchStatus && matchSpec;
  })
);

const columns = [
  { accessorKey: "name", header: "Freelancer" },
  { accessorKey: "speciality", header: "Especialidade" },
  { accessorKey: "rating", header: "Avaliação" },
  { accessorKey: "proposals", header: "Propostas" },
  { accessorKey: "profileStatus", header: "Perfil" },
  { accessorKey: "accountStatus", header: "Conta" },
  { accessorKey: "memberSince", header: "Membro desde" },
  { id: "actions", header: "" },
];
</script>

<template>
  <div class="space-y-6">
    <div class="flex items-center justify-between">
      <div>
        <h1 class="text-2xl font-bold text-white">Gerenciamento de Freelancers</h1>
        <p class="text-slate-400 text-sm mt-1">Gerir perfis, verificação e contas dos freelancers</p>
      </div>
    </div>

    <!-- Stats -->
    <div class="grid grid-cols-4 gap-4">
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-white">{{ freelancers.length }}</p>
        <p class="text-xs text-slate-400 mt-0.5">Total</p>
      </UCard>
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-emerald-400">
          {{ freelancers.filter((f) => f.profileStatus === "verified").length }}
        </p>
        <p class="text-xs text-slate-400 mt-0.5">Verificados</p>
      </UCard>
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-amber-400">
          {{ freelancers.filter((f) => f.profileStatus === "unverified").length }}
        </p>
        <p class="text-xs text-slate-400 mt-0.5">Por verificar</p>
      </UCard>
      <UCard class="border border-slate-800 text-center py-2">
        <p class="text-2xl font-bold text-rose-400">
          {{ freelancers.filter((f) => f.accountStatus === "suspended").length }}
        </p>
        <p class="text-xs text-slate-400 mt-0.5">Suspensos</p>
      </UCard>
    </div>

    <!-- Filters -->
    <UCard class="border border-slate-800">
      <div class="flex flex-col sm:flex-row gap-3">
        <UInput v-model="search" placeholder="Pesquisar por nome ou especialidade..." icon="i-lucide-search" class="flex-1" />
        <USelect v-model="filterSpeciality" :items="specialityOptions" value-key="value" label-key="label" class="w-56" />
        <USelect v-model="filterStatus" :items="statusOptions" value-key="value" label-key="label" class="w-44" />
      </div>
    </UCard>

    <!-- Table -->
    <UCard class="border border-slate-800">
      <template #header>
        <p class="text-sm text-slate-400">
          <span class="font-semibold text-white">{{ filtered.length }}</span> freelancer(s) encontrado(s)
        </p>
      </template>

      <UTable :data="filtered" :columns="columns">
        <template #name-cell="{ row }">
          <div class="flex items-center gap-3">
            <div class="h-9 w-9 rounded-full bg-violet-600 flex items-center justify-center text-sm font-bold text-white shrink-0">
              {{ row.original.name.charAt(0) }}
            </div>
            <div>
              <p class="font-medium text-white text-sm">{{ row.original.name }}</p>
              <p class="text-xs text-slate-500">{{ row.original.email }}</p>
            </div>
          </div>
        </template>

        <template #speciality-cell="{ row }">
          <span :class="['inline-flex items-center gap-1 rounded-full px-2.5 py-0.5 text-xs font-medium', specialityColors[row.original.speciality] ?? 'text-slate-400 bg-slate-700']">
            {{ row.original.speciality }}
          </span>
        </template>

        <template #rating-cell="{ row }">
          <div class="flex items-center gap-1.5">
            <template v-if="row.original.rating > 0">
              <Icon name="i-lucide-star" class="text-amber-400 text-sm" />
              <span class="text-sm font-semibold text-white">{{ row.original.rating }}</span>
            </template>
            <span v-else class="text-xs text-slate-500">Sem avaliação</span>
          </div>
        </template>

        <template #proposals-cell="{ row }">
          <UBadge color="neutral" variant="subtle" size="sm">{{ row.original.proposals }}</UBadge>
        </template>

        <template #profileStatus-cell="{ row }">
          <UBadge
            :color="row.original.profileStatus === 'verified' ? 'success' : 'warning'"
            variant="subtle"
            size="sm"
            :icon="row.original.profileStatus === 'verified' ? 'i-lucide-shield-check' : 'i-lucide-shield-alert'"
          >
            {{ row.original.profileStatus === "verified" ? "Verificado" : "Não verificado" }}
          </UBadge>
        </template>

        <template #accountStatus-cell="{ row }">
          <UBadge :color="accountStatusConfig[row.original.accountStatus].color" variant="subtle" size="sm">
            {{ accountStatusConfig[row.original.accountStatus].label }}
          </UBadge>
        </template>

        <template #memberSince-cell="{ row }">
          <span class="text-sm text-slate-400">{{ row.original.memberSince }}</span>
        </template>

        <template #actions-cell="{ row }">
          <div class="flex items-center justify-end gap-1.5">
            <UButton size="xs" color="neutral" variant="ghost" icon="i-lucide-eye" label="Ver" />
            <UButton v-if="row.original.profileStatus === 'unverified'" size="xs" color="success" variant="subtle" icon="i-lucide-shield-check" label="Verificar" />
            <UButton v-if="row.original.accountStatus === 'active'" size="xs" color="error" variant="subtle" icon="i-lucide-shield-off" label="Suspender" />
            <UButton v-if="row.original.accountStatus === 'suspended'" size="xs" color="warning" variant="subtle" icon="i-lucide-shield-check" label="Reativar" />
          </div>
        </template>
      </UTable>
    </UCard>
  </div>
</template>
