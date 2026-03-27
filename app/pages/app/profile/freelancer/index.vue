<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileFreelancer>
      <AppUiHeaderProfile> Sobre mim </AppUiHeaderProfile>
      <div class="flex flex-col min-h-40 items-start">
        <p class="text-justify text-slate-100">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores
          eligendi minus molestias minima est. Veniam cumque beatae, sapiente
          eaque maxime exercitationem officia harum eius maiores consectetur
          deleniti quam quasi inventore. Lorem ipsum dolor sit amet consectetur
          adipisicing elit. Dolores eligendi minus molestias minima est. Veniam
          cumque beatae, sapiente eaque maxime exercitationem officia harum eius
          maiores consectetur deleniti quam quasi inventore.
        </p>
        <UModal>
          <UButton
            label="Editar"
            class="mt-6"
            color="neutral"
            variant="outline"
          />
          <template #title>
            <AppUiHeaderProfile> Editar sobre mim </AppUiHeaderProfile>
          </template>
          <template #body>
            <UForm class="space-y-4 flex flex-col">
              <UTextarea
                :rows="12"
                :cols="20"
                class="w-full"
                placeholder="lorem ipsum dolor sit amet adiscipling.."
              />
            </UForm>
          </template>
          <template #footer>
            <AppUiButtonSidePrimary class="ml-auto" type="submit">
              Salvar
            </AppUiButtonSidePrimary>
          </template>
        </UModal>
      </div>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
