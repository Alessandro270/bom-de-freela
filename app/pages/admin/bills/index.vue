<script lang="ts" setup>
definePageMeta({ layout: "admin" });
useHead({ title: "Comprovativos — Admin | Bom de Freela" });

const activeTab = ref("pending");

const tabs = [
  { label: "Pendentes", value: "pending", icon: "i-lucide-clock" },
  { label: "Aprovados", value: "approved", icon: "i-lucide-check-circle" },
  { label: "Rejeitados", value: "rejected", icon: "i-lucide-x-circle" },
];

const allBills = [
  { id: "1", user: "João Martins", email: "jmartins@luanda.ao", type: "Transferência Bancária", amount: "KZ 45.000", project: "App Mobile de Delivery", submittedAt: "29 Mar 2026, 14:22", status: "pending" },
  { id: "2", user: "Carlos Neto", email: "cneto@empresa.ao", type: "Multicaixa Express", amount: "KZ 120.000", project: "Sistema de Gestão ERP", submittedAt: "29 Mar 2026, 11:05", status: "pending" },
  { id: "3", user: "Miguel Lopes", email: "mlopes@gmail.com", type: "Transferência Bancária", amount: "KZ 67.500", project: "Website Institucional", submittedAt: "28 Mar 2026, 20:10", status: "pending" },
  { id: "4", user: "Sofia Lima", email: "sofia.lima@outlook.com", type: "Multicaixa Express", amount: "KZ 35.000", project: "Design Logótipo", submittedAt: "28 Mar 2026, 09:45", status: "pending" },
  { id: "5", user: "Pedro Alves", email: "palves@tech.ao", type: "Transferência Bancária", amount: "KZ 200.000", project: "Plataforma E-Commerce", submittedAt: "27 Mar 2026, 15:30", status: "approved" },
  { id: "6", user: "Ana Ferreira", email: "ana.ferreira@email.com", type: "Multicaixa Express", amount: "KZ 55.000", project: "App Web Freelancer", submittedAt: "26 Mar 2026, 12:00", status: "approved" },
  { id: "7", user: "Laura Costa", email: "lcosta@agencia.ao", type: "Transferência Bancária", amount: "KZ 80.000", project: "Campanha Marketing", submittedAt: "25 Mar 2026, 16:00", status: "approved" },
  { id: "8", user: "Rui Baptista", email: "rbaptista@hotmail.com", type: "Multicaixa Express", amount: "KZ 15.000", project: "Consultoria TI", submittedAt: "24 Mar 2026, 10:20", status: "rejected" },
  { id: "9", user: "Marta Sousa", email: "marta.sousa@gmail.com", type: "Transferência Bancária", amount: "KZ 90.000", project: "API REST Backend", submittedAt: "23 Mar 2026, 08:50", status: "rejected" },
];

const filtered = computed(() => allBills.filter((b) => b.status === activeTab.value));
const countByStatus = (s: string) => allBills.filter((b) => b.status === s).length;

const columns = [
  { accessorKey: "user", header: "Utilizador" },
  { accessorKey: "type", header: "Método" },
  { accessorKey: "amount", header: "Valor" },
  { accessorKey: "project", header: "Projeto" },
  { accessorKey: "submittedAt", header: "Submetido" },
  { id: "actions", header: "" },
];
</script>

<template>
  <div class="space-y-6">
    <div>
      <h1 class="text-2xl font-bold text-white">Gerenciamento de Comprovativos</h1>
      <p class="text-slate-400 text-sm mt-1">Aprovar ou rejeitar comprovativos de pagamento submetidos</p>
    </div>

    <!-- Stats -->
    <div class="grid grid-cols-3 gap-4">
      <UCard class="border border-amber-500/20 bg-amber-500/5">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-2xl font-bold text-amber-400">{{ countByStatus("pending") }}</p>
            <p class="text-xs text-slate-400 mt-0.5">Pendentes</p>
          </div>
          <Icon name="i-lucide-clock" class="text-amber-400 text-2xl" />
        </div>
      </UCard>
      <UCard class="border border-emerald-500/20 bg-emerald-500/5">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-2xl font-bold text-emerald-400">{{ countByStatus("approved") }}</p>
            <p class="text-xs text-slate-400 mt-0.5">Aprovados</p>
          </div>
          <Icon name="i-lucide-check-circle" class="text-emerald-400 text-2xl" />
        </div>
      </UCard>
      <UCard class="border border-rose-500/20 bg-rose-500/5">
        <div class="flex items-center justify-between">
          <div>
            <p class="text-2xl font-bold text-rose-400">{{ countByStatus("rejected") }}</p>
            <p class="text-xs text-slate-400 mt-0.5">Rejeitados</p>
          </div>
          <Icon name="i-lucide-x-circle" class="text-rose-400 text-2xl" />
        </div>
      </UCard>
    </div>

    <!-- Tabs + Table -->
    <UCard class="border border-slate-800">
      <template #header>
        <div class="flex gap-1 border-b border-slate-800 -mx-4 -mt-4 px-4 pb-0">
          <button
            v-for="tab in tabs"
            :key="tab.value"
            @click="activeTab = tab.value"
            :class="[
              'flex items-center gap-1.5 px-4 py-3 text-sm font-medium border-b-2 transition-colors',
              activeTab === tab.value
                ? 'border-primary text-primary'
                : 'border-transparent text-slate-400 hover:text-slate-200',
            ]"
          >
            <Icon :name="tab.icon" class="text-sm" />
            {{ tab.label }}
            <UBadge
              :color="tab.value === 'pending' ? 'warning' : tab.value === 'approved' ? 'success' : 'error'"
              variant="subtle"
              size="xs"
            >
              {{ countByStatus(tab.value) }}
            </UBadge>
          </button>
        </div>
      </template>

      <UTable :data="filtered" :columns="columns">
        <template #user-cell="{ row }">
          <div class="flex items-center gap-3">
            <div class="h-8 w-8 rounded-full bg-slate-700 flex items-center justify-center text-xs font-bold text-white shrink-0">
              {{ row.original.user.charAt(0) }}
            </div>
            <div>
              <p class="font-medium text-white text-sm">{{ row.original.user }}</p>
              <p class="text-xs text-slate-500">{{ row.original.email }}</p>
            </div>
          </div>
        </template>

        <template #type-cell="{ row }">
          <div class="flex items-center gap-1.5">
            <Icon
              :name="row.original.type === 'Multicaixa Express' ? 'i-lucide-credit-card' : 'i-lucide-landmark'"
              class="text-slate-400 text-sm"
            />
            <span class="text-sm text-slate-300">{{ row.original.type }}</span>
          </div>
        </template>

        <template #amount-cell="{ row }">
          <span class="font-semibold text-white">{{ row.original.amount }}</span>
        </template>

        <template #project-cell="{ row }">
          <span class="text-sm text-slate-300 max-w-xs truncate block">{{ row.original.project }}</span>
        </template>

        <template #submittedAt-cell="{ row }">
          <span class="text-sm text-slate-400">{{ row.original.submittedAt }}</span>
        </template>

        <template #actions-cell="{ row }">
          <div class="flex items-center justify-end gap-1.5">
            <UButton size="xs" color="neutral" variant="ghost" icon="i-lucide-eye" label="Ver" />
            <template v-if="row.original.status === 'pending'">
              <UButton size="xs" color="success" variant="subtle" icon="i-lucide-check" label="Aprovar" />
              <UButton size="xs" color="error" variant="subtle" icon="i-lucide-x" label="Rejeitar" />
            </template>
          </div>
        </template>
      </UTable>

      <div v-if="filtered.length === 0" class="py-16 text-center">
        <Icon name="i-lucide-inbox" class="text-4xl text-slate-600 mx-auto mb-3" />
        <p class="text-slate-400 text-sm">Nenhum comprovativo neste estado.</p>
      </div>
    </UCard>
  </div>
</template>
