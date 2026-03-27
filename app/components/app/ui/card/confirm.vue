<script setup lang="ts">
defineProps<{
  message?: string;
  question?: string;
  confirmLabel?: string;
  cancelLabel?: string;
}>();

defineEmits<{
  confirm: [];
  cancel: [];
}>();
</script>

<template>
  <div class="flex flex-col gap-5 p-6">
    <!-- Header -->
    <div class="flex items-center gap-3">
      <div
        class="flex items-center justify-center w-10 h-10 rounded-lg bg-red-500/10 text-red-500 shrink-0"
      >
        <UIcon name="i-lucide-triangle-alert" class="size-5" />
      </div>
      <h2 class="text-base font-bold text-highlighted m-0">Confirmar Ação</h2>
    </div>

    <!-- Content -->
    <div class="flex flex-col gap-3">
      <p v-if="message" class="text-sm text-muted leading-relaxed m-0">
        {{ message }}
      </p>

      <div
        class="flex items-start gap-2.5 p-3 rounded-lg bg-elevated border border-default"
      >
        <UIcon
          name="i-lucide-circle-help"
          class="size-4 text-muted shrink-0 mt-0.5"
        />
        <p class="text-sm font-medium text-highlighted leading-snug m-0">
          {{ question ?? "Tem certeza que deseja continuar?" }}
        </p>
      </div>

      <div
        class="flex items-center gap-2 px-3 py-2 rounded-md bg-yellow-500/8 border border-yellow-500/25 text-xs text-yellow-700 dark:text-yellow-400"
      >
        <UIcon name="i-lucide-shield-alert" class="size-4 shrink-0" />
        <span
          >Esta ação <strong>não pode ser desfeita</strong> após a
          confirmação.</span
        >
      </div>
    </div>

    <!-- Footer -->
    <div class="flex justify-end gap-2 pt-4 border-t border-default">
      <UButton variant="ghost" color="neutral" @click="$emit('cancel')">
        <UIcon name="i-lucide-x" />
        {{ cancelLabel ?? "Cancelar" }}
      </UButton>
      <UButton color="error" @click="$emit('confirm')">
        <UIcon name="i-lucide-check" />
        {{ confirmLabel ?? "Confirmar" }}
      </UButton>
    </div>
  </div>
</template>
