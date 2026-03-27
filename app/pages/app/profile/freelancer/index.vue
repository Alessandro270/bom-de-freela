<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileFreelancer>
      <!-- Cabeçalho da secção -->
      <div class="flex items-center justify-between mb-4">
        <h2 class="text-sm font-semibold text-gray-700 dark:text-gray-300 uppercase tracking-wide">
          Sobre mim
        </h2>
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
              <UIcon name="i-lucide-user" class="h-4 w-4 text-gray-500" />
              <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">
                Editar sobre mim
              </span>
            </div>
          </template>
          <template #body>
            <UForm class="space-y-4">
              <UTextarea
                :rows="12"
                class="w-full"
                placeholder="Escreve algo sobre ti..."
              />
            </UForm>
          </template>
          <template #footer>
            <div class="flex justify-end">
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

      <!-- Conteúdo -->
      <p class="text-sm text-gray-700 dark:text-gray-300 leading-relaxed text-justify min-h-40">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores
        eligendi minus molestias minima est. Veniam cumque beatae, sapiente
        eaque maxime exercitationem officia harum eius maiores consectetur
        deleniti quam quasi inventore. Lorem ipsum dolor sit amet consectetur
        adipisicing elit. Dolores eligendi minus molestias minima est. Veniam
        cumque beatae, sapiente eaque maxime exercitationem officia harum eius
        maiores consectetur deleniti quam quasi inventore.
      </p>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
