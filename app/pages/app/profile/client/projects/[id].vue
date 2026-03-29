<script lang="ts" setup>
definePageMeta({ layout: "app" });

const status = ref<"em_andamento" | "concluido" | "pendente">("em_andamento");

const statusConfig = computed(
  () =>
    ({
      em_andamento: { label: "Em andamento", color: "warning" as const },
      concluido: { label: "Concluído", color: "success" as const },
      pendente: { label: "Pendente", color: "neutral" as const },
    })[status.value],
);

const proofFile = ref<File | null>(null);
</script>

<template>
  <AppLayoutWrapper>
    <div class="space-y-5 pb-10">
      <!-- Cabeçalho do projeto -->
      <UCard>
        <template #header>
          <div class="space-y-3 py-1">
            <div class="flex justify-between items-center">
              <h1
                class="text-xl font-semibold text-gray-900 dark:text-white leading-snug"
              >
                Desenvolvimento de plataforma e-commerce com Nuxt 3
              </h1>
              <UBadge :color="statusConfig.color" variant="soft" size="md">
                {{ statusConfig.label }}
              </UBadge>
            </div>
            <div class="flex flex-wrap gap-2">
              <UBadge color="neutral" variant="outline" size="sm"
                >Tecnologia</UBadge
              >
              <UBadge color="neutral" variant="outline" size="sm"
                >Desenvolvimento Web</UBadge
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
        <UCard>
          <AppUiHeaderDescGroup
            title="Valor do contrato"
            description="AOA 320.000"
          />
        </UCard>
        <UCard>
          <AppUiHeaderDescGroup
            title="Prazo de entrega"
            description="30 dias"
          />
        </UCard>
        <UCard>
          <AppUiHeaderDescGroup title="Aceite em" description="10/03/2026" />
        </UCard>
      </div>

      <!-- Partes envolvidas -->
      <div class="grid grid-cols-2 gap-4">
        <AppUiCardUserInfo
          role="cliente"
          first-name="Alessandro"
          last-name="Almeida"
          nif="5 417 835 LA 042"
          email="a.almeida@email.ao"
          phone="+244 923 456 789"
          location="Luanda, Angola"
        />
        <AppUiCardUserInfo
          role="freelancer"
          first-name="Marcos"
          last-name="Silva"
          nif="6 832 017 LB 118"
          email="m.silva@freelancer.ao"
          phone="+244 912 345 678"
          location="Luanda, Angola"
        />
      </div>

      <!-- Detalhes do contrato -->
      <UCard>
        <template #header>
          <AppUiHeaderSubtle size="md">Detalhes do contrato</AppUiHeaderSubtle>
        </template>

        <div class="space-y-5">
          <!-- Datas -->
          <div class="grid grid-cols-2 gap-x-4 gap-y-4">
            <AppUiHeaderDescGroup
              reverse
              title="Data de início"
              description="10 de Março, 2026"
            />
            <AppUiHeaderDescGroup
              reverse
              title="Conclusão prevista"
              description="30 de Março, 2026"
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
            <p
              class="text-xs text-gray-400 dark:text-gray-500 uppercase tracking-wide font-medium"
            >
              Descrição
            </p>
            <p class="text-sm text-gray-700 dark:text-gray-300 leading-relaxed">
              Desenvolvimento completo de uma plataforma de e-commerce com
              sistema de autenticação, gestão de encomendas, pagamentos
              integrados e painel administrativo. O projeto inclui design
              responsivo e integração com APIs de pagamento locais.
            </p>
          </div>

          <USeparator />

          <!-- Habilidades -->
          <div class="space-y-2">
            <p
              class="text-xs text-gray-400 dark:text-gray-500 uppercase tracking-wide font-medium"
            >
              Habilidades requeridas
            </p>
            <div class="flex flex-wrap gap-2">
              <UBadge color="neutral" variant="outline" size="sm"
                >Vue.js</UBadge
              >
              <UBadge color="neutral" variant="outline" size="sm"
                >Node.js</UBadge
              >
              <UBadge color="neutral" variant="outline" size="sm"
                >PostgreSQL</UBadge
              >
              <UBadge color="neutral" variant="outline" size="sm"
                >Nuxt.js</UBadge
              >
              <UBadge color="neutral" variant="outline" size="sm"
                >API REST</UBadge
              >
            </div>
          </div>

          <USeparator />

          <!-- Acções -->
          <div class="flex items-center justify-between gap-4">
            <!-- Cancelar contrato -->
            <UModal>
              <UButton
                color="error"
                variant="subtle"
                icon="i-lucide-ban"
                label="Cancelar contrato"
              />
              <template #header>
                <div class="flex items-center gap-2">
                  <UIcon
                    name="i-lucide-alert-triangle"
                    class="h-4 w-4 text-red-500"
                  />
                  <span
                    class="text-sm font-semibold text-red-600 dark:text-red-400"
                  >
                    Cancelar contrato
                  </span>
                </div>
              </template>
              <template #body>
                <p class="text-sm text-gray-600 dark:text-gray-400">
                  Tens a certeza que queres cancelar este contrato? Esta ação é
                  irreversível e pode ter implicações legais e financeiras.
                </p>
              </template>
              <template #footer>
                <div class="flex items-center justify-end gap-2 w-full">
                  <UButton color="neutral" variant="ghost" label="Voltar" />
                  <UButton
                    color="error"
                    variant="solid"
                    icon="i-lucide-ban"
                    label="Confirmar cancelamento"
                  />
                </div>
              </template>
            </UModal>

            <!-- Enviar comprovativo (visível quando concluído) -->
            <div v-if="status === 'concluido'" class="flex items-center gap-3">
              <UBadge
                color="success"
                variant="soft"
                icon="i-lucide-check-circle"
                size="sm"
              >
                Projeto concluído
              </UBadge>
              <UModal>
                <UButton
                  color="primary"
                  variant="solid"
                  icon="i-lucide-upload"
                  label="Enviar comprovativo de pagamento"
                />
                <template #header>
                  <div class="flex items-center gap-2">
                    <UIcon
                      name="i-lucide-file-check"
                      class="h-4 w-4 text-gray-500"
                    />
                    <span
                      class="text-sm font-semibold text-gray-700 dark:text-gray-300"
                    >
                      Enviar comprovativo de pagamento
                    </span>
                  </div>
                </template>
                <template #body>
                  <div class="space-y-4">
                    <p class="text-sm text-gray-600 dark:text-gray-400">
                      Faz o upload do comprovativo de transferência bancária ou
                      recibo de pagamento referente a este projeto.
                    </p>
                    <UFormField label="Comprovativo" name="proof">
                      <UInput
                        type="file"
                        class="w-full"
                        accept=".pdf,.jpg,.jpeg,.png"
                      />
                    </UFormField>
                    <UFormField label="Observações" name="notes">
                      <UTextarea
                        class="w-full"
                        placeholder="Adiciona alguma nota sobre o pagamento (opcional)..."
                        :rows="3"
                      />
                    </UFormField>
                  </div>
                </template>
                <template #footer>
                  <div class="flex justify-end">
                    <UButton
                      type="submit"
                      color="primary"
                      variant="solid"
                      icon="i-lucide-send"
                      label="Enviar comprovativo"
                    />
                  </div>
                </template>
              </UModal>
            </div>

            <!-- Enquanto não concluído: mostrar comprovativo desabilitado com tooltip -->
            <div v-else>
              <UTooltip
                text="Disponível após o projeto ser marcado como concluído"
              >
                <UButton
                  color="primary"
                  variant="soft"
                  icon="i-lucide-upload"
                  label="Enviar comprovativo de pagamento"
                  disabled
                />
              </UTooltip>
            </div>
          </div>
        </div>
      </UCard>
    </div>
  </AppLayoutWrapper>
</template>
