<script lang="ts" setup>
definePageMeta({ layout: "admin" });
useHead({ title: "Dashboard — Admin | Bom de Freela" });

const kpis = [
  {
    label: "Total de Contas",
    value: "1.248",
    delta: "+12% este mês",
    icon: "i-lucide-users",
    color: "text-blue-400",
    bg: "bg-blue-500/10",
  },
  {
    label: "Contas Pendentes",
    value: "34",
    delta: "Aguardando verificação",
    icon: "i-lucide-user-x",
    color: "text-amber-400",
    bg: "bg-amber-500/10",
  },
  {
    label: "Comprovativos",
    value: "18",
    delta: "Aguardando aprovação",
    icon: "i-lucide-receipt",
    color: "text-rose-400",
    bg: "bg-rose-500/10",
  },
  {
    label: "Projetos Ativos",
    value: "203",
    delta: "+5 esta semana",
    icon: "i-lucide-folder-open",
    color: "text-emerald-400",
    bg: "bg-emerald-500/10",
  },
];

const pendingApprovals = [
  { id: "1", user: "João Martins", type: "Comprovativo", value: "KZ 45.000", submittedAt: "Hoje, 14:22" },
  { id: "2", user: "Ana Ferreira", type: "Verificação de conta", value: "—", submittedAt: "Hoje, 11:05" },
  { id: "3", user: "Carlos Neto", type: "Comprovativo", value: "KZ 120.000", submittedAt: "Ontem, 18:40" },
  { id: "4", user: "Beatriz Silva", type: "Verificação de conta", value: "—", submittedAt: "Ontem, 09:15" },
  { id: "5", user: "Miguel Lopes", type: "Comprovativo", value: "KZ 67.500", submittedAt: "28 Mar, 20:10" },
];

const recentActivity = [
  { action: "Comprovativo aprovado", user: "Pedro Alves", time: "há 2 min", icon: "i-lucide-check-circle", color: "text-emerald-400" },
  { action: "Nova conta registada", user: "Sofia Lima", time: "há 15 min", icon: "i-lucide-user-plus", color: "text-blue-400" },
  { action: "Projeto publicado", user: "Tecnologias Luanda Lda.", time: "há 32 min", icon: "i-lucide-folder-plus", color: "text-purple-400" },
  { action: "Comprovativo rejeitado", user: "Rui Baptista", time: "há 1h", icon: "i-lucide-x-circle", color: "text-rose-400" },
  { action: "Conta suspensa", user: "Teste Spam", time: "há 2h", icon: "i-lucide-shield-off", color: "text-amber-400" },
];

const approvalColumns = [
  { accessorKey: "user", header: "Utilizador" },
  { accessorKey: "type", header: "Tipo" },
  { accessorKey: "value", header: "Valor" },
  { accessorKey: "submittedAt", header: "Submetido" },
  { id: "actions", header: "" },
];
</script>

<template>
  <div class="space-y-6">
    <!-- Header -->
    <div>
      <h1 class="text-2xl font-bold text-white">Dashboard</h1>
      <p class="text-slate-400 text-sm mt-1">Visão geral da plataforma Bom de Freela</p>
    </div>

    <!-- KPI Cards -->
    <div class="grid grid-cols-1 sm:grid-cols-2 xl:grid-cols-4 gap-4">
      <UCard v-for="kpi in kpis" :key="kpi.label" class="border border-slate-800">
        <div class="flex items-start justify-between gap-4">
          <div class="space-y-1">
            <p class="text-xs font-medium text-slate-400 uppercase tracking-wider">{{ kpi.label }}</p>
            <p class="text-3xl font-bold text-white">{{ kpi.value }}</p>
            <p class="text-xs text-slate-500">{{ kpi.delta }}</p>
          </div>
          <div :class="['p-3 rounded-xl', kpi.bg]">
            <Icon :name="kpi.icon" :class="['text-xl', kpi.color]" />
          </div>
        </div>
      </UCard>
    </div>

    <!-- Main Content Grid -->
    <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
      <!-- Pending Approvals Table -->
      <div class="lg:col-span-2">
        <UCard class="border border-slate-800">
          <template #header>
            <div class="flex items-center justify-between">
              <h2 class="text-base font-semibold text-white">Aprovações Pendentes</h2>
              <UBadge color="warning" variant="subtle" size="sm">
                {{ pendingApprovals.length }} pendentes
              </UBadge>
            </div>
          </template>

          <UTable :data="pendingApprovals" :columns="approvalColumns">
            <template #user-cell="{ row }">
              <div class="flex items-center gap-2.5">
                <div class="h-8 w-8 rounded-full bg-slate-700 flex items-center justify-center text-xs font-bold text-white shrink-0">
                  {{ row.original.user.charAt(0) }}
                </div>
                <span class="font-medium text-white text-sm">{{ row.original.user }}</span>
              </div>
            </template>
            <template #type-cell="{ row }">
              <UBadge
                :color="row.original.type === 'Comprovativo' ? 'info' : 'secondary'"
                variant="subtle"
                size="xs"
              >
                {{ row.original.type }}
              </UBadge>
            </template>
            <template #value-cell="{ row }">
              <span class="font-medium text-white text-sm">{{ row.original.value }}</span>
            </template>
            <template #submittedAt-cell="{ row }">
              <span class="text-sm text-slate-400">{{ row.original.submittedAt }}</span>
            </template>
            <template #actions-cell>
              <div class="flex gap-1.5 justify-end">
                <UButton size="xs" color="success" variant="subtle" icon="i-lucide-check" label="Aprovar" />
                <UButton size="xs" color="error" variant="subtle" icon="i-lucide-x" label="Rejeitar" />
              </div>
            </template>
          </UTable>

          <template #footer>
            <NuxtLink to="/admin/bills" class="text-xs text-primary hover:underline">
              Ver todos os comprovativos →
            </NuxtLink>
          </template>
        </UCard>
      </div>

      <!-- Recent Activity Feed -->
      <div>
        <UCard class="border border-slate-800 h-full">
          <template #header>
            <h2 class="text-base font-semibold text-white">Atividade Recente</h2>
          </template>
          <div class="space-y-4">
            <div v-for="(item, idx) in recentActivity" :key="idx" class="flex items-start gap-3">
              <div class="mt-0.5 h-7 w-7 rounded-full bg-slate-800 flex items-center justify-center shrink-0">
                <Icon :name="item.icon" :class="['text-sm', item.color]" />
              </div>
              <div class="min-w-0">
                <p class="text-sm text-white leading-snug">{{ item.action }}</p>
                <p class="text-xs text-slate-500 mt-0.5">{{ item.user }} · {{ item.time }}</p>
              </div>
            </div>
          </div>
        </UCard>
      </div>
    </div>
  </div>
</template>
