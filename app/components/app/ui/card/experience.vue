<script setup lang="ts">
const props = defineProps<{
  role: string;
  company: string;
  startYear: string;
  endYear: string;
  edit?: boolean;
}>();
</script>

<template>
  <li class="py-4 flex items-start justify-between gap-6">
    <!-- Avatar + info -->
    <div class="flex items-center gap-4">
      <UAvatar
        :alt="company"
        size="md"
        class="bg-violet-600 shrink-0"
      />
      <div class="space-y-0.5">
        <p class="text-sm font-semibold text-gray-900 dark:text-white">
          {{ role }}
        </p>
        <p class="text-sm text-gray-500 dark:text-gray-400">{{ company }}</p>
      </div>
    </div>

    <!-- Período + editar -->
    <div class="flex items-center gap-4 shrink-0">
      <span class="text-sm text-gray-500 dark:text-gray-400">
        {{ startYear }} – {{ endYear }}
      </span>

      <UModal v-if="edit">
        <UButton
          size="xs"
          color="neutral"
          variant="ghost"
          icon="i-lucide-pencil"
          label="Editar"
        />
        <template #header>
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-briefcase" class="h-4 w-4 text-gray-500" />
            <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">
              Editar experiência
            </span>
          </div>
        </template>
        <template #body>
          <UForm class="space-y-3">
            <UFormField label="Cargo" name="function">
              <UInput class="w-full" placeholder="UI/UX Designer..." />
            </UFormField>
            <UFormField label="Empresa" name="company">
              <UInput class="w-full" placeholder="Nome da empresa" />
            </UFormField>
            <div class="grid grid-cols-2 gap-4">
              <UFormField label="Início" name="start">
                <UInputDate class="w-full" />
              </UFormField>
              <UFormField label="Fim" name="end">
                <UInputDate class="w-full" />
              </UFormField>
            </div>
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
  </li>
</template>
