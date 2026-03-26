<script lang="ts" setup>
const skills = reactive([
  {
    id: 1,
    name: "Python",
    value: 4,
  },
  {
    id: 2,
    name: "JavaScript",
    value: 5,
  },
  {
    id: 3,
    name: "CSS",
    value: 4,
  },
  {
    id: 4,
    name: "HTML",
    value: 5,
  },
]);
const tags = ref([]);
</script>

<template>
  <div class="space-y-6 font-google w-5xl mx-auto">
    <div
      class="bg-slate-950 flex justify-between items-start rounded-md px-8 py-7 space-y-4"
    >
      <div class="flex flex-col w-full space-y-4">
        <div class="flex justify-between items-start w-full h-full">
          <div class="space-x-8 flex">
            <AppUiButtonSquareAvatar name="Alessandro Almeida" />
            <div class="flex space-y-0.5 flex-col">
              <h1 class="text-3xl text-slate-200">Alessandro Almeida</h1>
              <span class="text-xl font-medium text-slate-400">
                Desenvolvedor backend
              </span>
              <div class="flex h-6 items-center space-x-2">
                <UiRating :value="4" />
              </div>
            </div>
          </div>
          <div class="flex flex-col w-1/5 justify-between h-26 items-end">
            <AppUiButtonSideDesc title="Membro desde" value="2023" />
          </div>
        </div>

        <hr class="text-slate-700" />
        <div class="space-y-2 flex justify-between">
          <div class="flex space-x-4 items-center">
            <i class="text-slate-300 inline-block font-semibold">
              habilidades:
            </i>
            <AppUiButtonTag>Python</AppUiButtonTag>
            <AppUiButtonTag>Backend</AppUiButtonTag>
            <AppUiButtonTag>Pwa</AppUiButtonTag>
          </div>
          <UModal>
            <UButton label="Editar" color="neutral" variant="outline" />
            <template #header>
              <AppUiHeaderProfile
                >Editar habilidades principais</AppUiHeaderProfile
              >
            </template>
            <template #body>
              <UForm class="space-y-5">
                <UFormField label="Habilidades">
                  <UInputTags v-model="tags" class="w-full" />
                </UFormField>
                <div class="flex space-x-3 justify-end">
                  <AppUiButtonSidePrimary type="submit">
                    Salvar
                  </AppUiButtonSidePrimary>
                </div>
              </UForm>
            </template>
          </UModal>
        </div>
      </div>
    </div>
    <AppUiNavBar
      :items="[
        { to: '/app/profile/freelancer/', label: 'Sobre mim' },
        { to: 'projects', label: 'Projetos' },
        { to: 'reviews', label: 'Avaliações' },
        { to: 'proposals', label: 'Propostas' },
        { to: 'skills', label: 'Habilidades' },
        { to: 'experience', label: 'Experiencia' },
      ]"
    />
    <div class="bg-slate-950 min-h-60 rounded-md px-6 py-7 space-y-4">
      <slot />
    </div>
  </div>
</template>
