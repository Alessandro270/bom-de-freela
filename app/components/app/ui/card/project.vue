<script lang="ts" setup>
defineProps<{
  title: string;
  acceptedAt: string;
  deadline: string;
  clientName: string;
  status: "em_progresso" | "concluido";
  id: string | number;
  to: string;
}>();
</script>

<template>
  <div class="py-4 flex items-start justify-between gap-6">
    <!-- Info -->
    <div class="space-y-2 flex-1 min-w-0">
      <p
        class="text-sm font-semibold text-gray-900 dark:text-white leading-snug"
      >
        {{ title }}
      </p>
      <div class="flex items-center gap-3">
        <UAvatar :alt="clientName" size="xs" class="bg-violet-600 shrink-0" />
        <span class="text-sm font-medium text-gray-700 dark:text-gray-300">
          {{ clientName }}
        </span>
      </div>
      <div class="flex items-center gap-4">
        <span class="text-xs text-gray-400 dark:text-gray-500">
          Aceite em:
          <span class="text-gray-600 dark:text-gray-300 font-medium">{{
            acceptedAt
          }}</span>
        </span>
        <span class="text-xs text-gray-400 dark:text-gray-500">
          Deadline:
          <span class="text-gray-600 dark:text-gray-300 font-medium">{{
            deadline
          }}</span>
        </span>
      </div>
    </div>

    <!-- Estado + link -->
    <div class="flex flex-col items-end gap-3 shrink-0">
      <UBadge
        :color="status === 'concluido' ? 'success' : 'warning'"
        variant="subtle"
        size="sm"
      >
        {{ status === "concluido" ? "Concluído" : "Em progresso" }}
      </UBadge>
      <UButton
        size="xs"
        color="neutral"
        variant="ghost"
        label="Ver detalhes"
        icon="i-lucide-arrow-up-right"
        trailing
        :to="to"
      />
    </div>
  </div>
</template>
