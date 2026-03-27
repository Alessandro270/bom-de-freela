<script lang="ts" setup>
defineProps<{
  id: string | number;
  jobTitle: string;
  clientName: string;
  sentAt: string;
  value: string;
  status: "pendente" | "aceite" | "rejeitado";
}>();

const statusColor = (status: string) => {
  if (status === "aceite") return "success";
  if (status === "rejeitado") return "error";
  return "neutral";
};

const statusLabel = (status: string) => {
  if (status === "aceite") return "Aceite";
  if (status === "rejeitado") return "Rejeitado";
  return "Pendente";
};
</script>

<template>
  <div class="py-4 flex items-start justify-between gap-6">
    <!-- Info -->
    <div class="space-y-2 flex-1 min-w-0">
      <p class="text-sm font-semibold text-gray-900 dark:text-white leading-snug">
        {{ jobTitle }}
      </p>
      <div class="flex items-center gap-3">
        <UAvatar :alt="clientName" size="xs" class="bg-violet-600 shrink-0" />
        <span class="text-sm font-medium text-gray-700 dark:text-gray-300">
          {{ clientName }}
        </span>
      </div>
      <div class="flex items-center gap-4">
        <span class="text-xs text-gray-400 dark:text-gray-500">
          Enviado em:
          <span class="text-gray-600 dark:text-gray-300 font-medium">{{ sentAt }}</span>
        </span>
        <span class="text-xs text-gray-400 dark:text-gray-500">
          Valor:
          <span class="text-gray-600 dark:text-gray-300 font-medium">{{ value }}</span>
        </span>
      </div>
    </div>

    <!-- Estado + editar -->
    <div class="flex flex-col items-end gap-3 shrink-0">
      <UBadge
        :color="statusColor(status)"
        variant="subtle"
        size="sm"
      >
        {{ statusLabel(status) }}
      </UBadge>

      <UModal>
        <UButton
          size="xs"
          color="neutral"
          variant="ghost"
          icon="i-lucide-pencil"
          label="Editar"
        />
        <template #header>
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-file-text" class="h-4 w-4 text-gray-500" />
            <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">
              Editar proposta
            </span>
          </div>
        </template>
        <template #body>
          <UForm class="space-y-4">
            <UFormField label="Descrição" name="description">
              <UTextarea class="w-full" placeholder="Descrição da proposta" />
            </UFormField>
            <UFormField label="Preço inicial" name="startPrice">
              <UInputNumber
                class="w-full"
                placeholder="575,000.00 kz"
                orientation="vertical"
              />
            </UFormField>
          </UForm>
        </template>
        <template #footer>
          <div class="flex items-center justify-between w-full">
            <UButton
              color="error"
              variant="ghost"
              icon="i-lucide-trash-2"
              label="Eliminar"
            />
            <UButton
              type="submit"
              color="primary"
              variant="solid"
              icon="i-lucide-save"
              label="Salvar"
            />
          </div>
        </template>
      </UModal>
    </div>
  </div>
</template>
