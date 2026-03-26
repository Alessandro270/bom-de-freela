<script lang="ts" setup>
definePageMeta({ layout: "app" });

const status = ref<"em_andamento" | "concluido" | "pendente">("em_andamento");

const statusConfig = computed(
  () =>
    ({
      em_andamento: { label: "Em andamento", color: "info" as const },
      concluido: { label: "Concluído", color: "success" as const },
      pendente: { label: "Pendente", color: "warning" as const },
    })[status.value],
);

async function marcarConcluido() {
  status.value = "concluido";
}
</script>

<template>
  <AppLayoutWrapper>
    <div class="space-y-5 pb-10">
      <!-- Breadcrumb + estado -->
      <div class="flex items-center justify-between">
        <nav class="flex items-center space-x-1 text-xs text-slate-500">
          <span class="hover:text-slate-300 cursor-pointer transition-colors"
            >Projectos</span
          >
          <span class="text-slate-600">›</span>
          <span class="text-slate-300">Detalhes do projecto</span>
        </nav>
        <UBadge :color="statusConfig.color" variant="soft" size="md">
          {{ statusConfig.label }}
        </UBadge>
      </div>

      <!-- Cabeçalho do projecto -->
      <UCard variant="subtle" class="border border-white/5">
        <template #header>
          <div class="space-y-3 py-1">
            <h1 class="text-xl font-semibold text-slate-100 leading-snug">
              Desenvolvimento de uma plataforma de freelancing digital
            </h1>
            <div class="flex flex-wrap gap-2">
              <UBadge color="neutral" variant="outline" size="sm"
                >Tecnologia</UBadge
              >
              <UBadge color="neutral" variant="outline" size="sm"
                >Desenvolvimento web</UBadge
              >
              <UBadge color="neutral" variant="outline" size="sm"
                >Prazo: 30 dias</UBadge
              >
            </div>
          </div>
        </template>
      </UCard>

      <!-- Métricas -->
      <div class="grid grid-cols-3 gap-4">
        <UCard variant="subtle" class="border border-white/5">
          <AppUiHeaderDescGroup
            title="Valor do contrato"
            description="AOA 250.000"
          />
        </UCard>
        <UCard variant="subtle" class="border border-white/5">
          <AppUiHeaderDescGroup
            title="Prazo de entrega"
            description="30 dias"
          />
        </UCard>
        <UCard variant="subtle" class="border border-white/5">
          <AppUiHeaderDescGroup title="Aceite em" description="15/03/2026" />
        </UCard>
      </div>

      <div class="grid grid-cols-2 gap-4">
        <AppUiCardUserInfo
          role="cliente"
          first-name="António"
          last-name="Costa"
          nif="5 417 835 LA 042"
          email="a.costa@empresa.ao"
          phone="+244 923 456 789"
          location="Luanda, Angola"
        />
        <AppUiCardUserInfo
          role="freelancer"
          first-name="Manuel"
          last-name="Silva"
          nif="6 832 017 LB 118"
          email="m.silva@freelancer.ao"
          phone="+244 912 345 678"
          location="Luanda, Angola"
        />
      </div>

      <!-- Descrição + Habilidades + Datas -->
      <UCard variant="subtle" class="border border-white/5">
        <template #header>
          <AppUiHeaderSubtle size="md">Detalhes do contrato</AppUiHeaderSubtle>
        </template>

        <div class="space-y-5">
          <!-- Datas -->
          <div class="grid grid-cols-2 gap-x-4 gap-y-4">
            <AppUiHeaderDescGroup
              reverse
              title="Data de início"
              description="15 de Março, 2026"
            />
            <AppUiHeaderDescGroup
              reverse
              title="Conclusão prevista"
              description="14 de Abril, 2026"
            />
            <AppUiHeaderDescGroup
              reverse
              title="Estado"
              description="Em andamento"
            />
            <AppUiHeaderDescGroup
              reverse
              title="Terminado em"
              description="—"
            />
          </div>

          <USeparator />

          <!-- Descrição -->
          <div class="space-y-1.5">
            <p class="text-xs text-slate-400 font-google">Descrição</p>
            <p
              class="text-sm text-slate-200 font-google font-light leading-relaxed"
            >
              Desenvolvimento completo de uma plataforma de freelancing digital
              com sistema de autenticação, gestão de projectos, pagamentos
              integrados e painel administrativo. O projecto inclui design
              responsivo, optimização para motores de busca e integração com
              APIs de pagamento locais angolanas.
            </p>
          </div>

          <USeparator />

          <!-- Habilidades -->
          <div class="space-y-2">
            <p class="text-xs text-slate-400 font-google">
              Habilidades requeridas
            </p>
            <div class="flex flex-wrap gap-2">
              <UBadge color="primary" variant="soft" size="sm">Vue.js</UBadge>
              <UBadge color="primary" variant="soft" size="sm">Node.js</UBadge>
              <UBadge color="primary" variant="soft" size="sm"
                >PostgreSQL</UBadge
              >
              <UBadge color="primary" variant="soft" size="sm"
                >UI/UX Design</UBadge
              >
              <UBadge color="primary" variant="soft" size="sm">API REST</UBadge>
              <UBadge color="primary" variant="soft" size="sm">Nuxt.js</UBadge>
            </div>
          </div>

          <USeparator />

          <!-- Acções -->
          <div class="flex items-center gap-3 pt-1">
            <UButton
              color="primary"
              :disabled="status === 'concluido'"
              @click="marcarConcluido"
            >
              {{
                status === "concluido"
                  ? "Projecto concluído"
                  : "Marcar como concluído"
              }}
            </UButton>
          </div>
        </div>
      </UCard>
    </div>
  </AppLayoutWrapper>
</template>
