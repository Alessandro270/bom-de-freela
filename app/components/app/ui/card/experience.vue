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
  <li class="py-4 justify-between w-full items-start flex space-x-10">
    <div class="flex items-start w-full justify-between">
      <div class="flex items-center space-x-4 uppercase">
        <AppUiButtonSmallAvatar :name="company" />

        <div class="text-sm space-y-0.5">
          <h3 class="text-sm font-medium">
            {{ role }}
          </h3>

          <span class="text-sm text-slate-300">
            {{ company }}
          </span>
        </div>
      </div>

      <span class="text-sm text-slate-300">
        {{ startYear }} - {{ endYear }}
      </span>
    </div>

    <UModal v-if="edit">
      <UButton label="Editar" color="neutral" variant="outline" />

      <template #header>
        <AppUiHeaderProfile>Editar experiencia</AppUiHeaderProfile>
      </template>

      <template #body>
        <UForm class="space-y-3">
          <UFormField label="Cargo" name="function">
            <UInput class="w-full" placeholder="UI/UX.." />
          </UFormField>
          <UFormField label="Empresa" name="company">
            <UInput class="w-full" placeholder="exemplo" />
          </UFormField>
          <div class="flex space-x-4 mb-4">
            <UFormField label="Inicio" name="start">
              <UInputDate />
            </UFormField>
            <UFormField label="Fim" name="end">
              <UInputDate />
            </UFormField>
          </div>
          <div class="flex space-x-3 justify-end">
            <AppUiButtonSideSecondary>Eliminar</AppUiButtonSideSecondary>
            <AppUiButtonSidePrimary>Salvar</AppUiButtonSidePrimary>
          </div>
        </UForm>
      </template>
    </UModal>
  </li>
</template>
