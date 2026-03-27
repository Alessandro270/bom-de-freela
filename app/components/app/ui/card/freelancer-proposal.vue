<script lang="ts" setup>
defineProps<{
  name: string;
  sentAt: string;
  value: string;
}>();
</script>

<template>
  <UCard>
    <div class="flex items-start gap-4">
      <!-- Avatar -->
      <UAvatar :alt="name" size="md" class="bg-violet-600 shrink-0" />

      <!-- Content -->
      <div class="flex-1 min-w-0 space-y-2">
        <!-- Header: nome + valor -->
        <div class="flex items-start justify-between gap-4">
          <div>
            <p class="text-sm font-semibold text-gray-900 dark:text-white">
              {{ name }}
            </p>
            <p class="text-xs text-gray-400 dark:text-gray-500 mt-0.5">
              Enviado em {{ sentAt }}
            </p>
          </div>
          <span
            class="text-sm font-semibold text-violet-600 dark:text-violet-400 shrink-0"
          >
            {{ value }}
          </span>
        </div>

        <!-- Descrição -->
        <p
          class="text-sm text-gray-600 dark:text-gray-400 leading-relaxed text-justify"
        >
          <slot />
        </p>

        <!-- Ações -->
        <div class="flex items-center gap-2 pt-1">
          <UButton
            size="xs"
            color="success"
            variant="soft"
            icon="i-lucide-check"
            label="Aceitar"
          />
          <UButton
            size="xs"
            color="error"
            variant="soft"
            icon="i-lucide-x"
            label="Rejeitar"
          />
        </div>
      </div>
    </div>
  </UCard>
</template>
