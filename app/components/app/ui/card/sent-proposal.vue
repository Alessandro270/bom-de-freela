<script lang="ts" setup>
defineProps<{
  id: string | number;
  jobTitle: string;
  clientName: string;
  sentAt: string;
  value: string;
  status: "pendente" | "aceite" | "rejeitado";
}>();
</script>

<template>
  <div class="py-4 flex items-start justify-between gap-6">
    <div class="space-y-3 flex-1 min-w-0">
      <h3 class="text-slate-100 font-bold text-sm uppercase leading-snug">
        {{ jobTitle }}
      </h3>
      <div class="flex gap-4 items-center">
        <AppUiButtonSmallAvatar :name="clientName" class="" />
        <div>
          <span class="text-slate-200 text-sm font-medium">
            {{ clientName }}
          </span>
          <div class="space-x-4">
            <span class="text-slate-400 text-xs italic">
              enviado em:
              <span class="text-slate-200 not-italic font-medium">
                {{ sentAt }}
              </span>
            </span>
            <span class="text-slate-400 text-xs italic">
              valor:
              <span class="text-slate-200 not-italic font-medium">
                {{ value }}
              </span>
            </span>
          </div>
        </div>
      </div>
    </div>

    <div class="text-right space-y-2 flex flex-col justify-between h-18">
      <p class="text-slate-400 text-xs italic">
        estado:
        <span
          class="not-italic font-medium capitalize"
          :class="{
            'text-slate-300': status === 'pendente',
            'text-purple-400': status === 'aceite',
            'text-red-400': status === 'rejeitado',
          }"
        >
          {{ status }}
        </span>
      </p>
      <div class="flex items-center justify-end gap-2">
        <UModal>
          <UButton label="Editar proposta" color="neutral" variant="subtle" />
          <template #header>
            <AppUiHeaderProfile>Editar proposta</AppUiHeaderProfile>
          </template>
          <template #body>
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
          </template>
        </UModal>
      </div>
    </div>
  </div>
</template>
