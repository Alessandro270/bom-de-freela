<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutWrapper title="Nova proposta">
    <UForm class="space-y-4">
      <UFormField label="Descrição" name="description">
        <UTextarea class="w-full" placeholder="Descrição da proposta" />
      </UFormField>

      <UFormField label="Preco inicial" name="startPrice">
        <UInputNumber
          class="w-full"
          placeholder="575,000.00 kz"
          orientation="vertical"
        />
      </UFormField>
      <div class="flex space-x-3 justify-end">
        <AppUiButtonSideSecondary>Eliminar</AppUiButtonSideSecondary>
        <AppUiButtonSidePrimary>Salvar</AppUiButtonSidePrimary>
      </div>
    </UForm>
  </AppLayoutWrapper>
</template>
