<script lang="ts" setup>
definePageMeta({ layout: "app" });

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
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileFreelancer>
      <AppUiHeaderProfile class="flex justify-between">
        <span>Habilidades</span>
        <span class="text-slate-400">(5)</span>
      </AppUiHeaderProfile>
      <ul class="*:not-last:border-b *:not-last:border-slate-700">
        <AppUiCardSkill
          v-for="skill in skills"
          :key="skill.id"
          :value="skill.value"
        >
          {{ skill.name }}
        </AppUiCardSkill>
      </ul>
      <UModal>
        <UButton label="Editar" color="neutral" variant="subtle" />
        <template #body>
          <AppLayoutWrapper title="Editar habilidade">
            <UForm class="space-y-5">
              <UFormField
                :label="skill.name"
                orientation="horizontal"
                :key="skill.id"
                v-for="skill in skills"
              >
                <AppUiButtonRating :rating="skill.value" />
              </UFormField>
              <div class="flex space-x-3 justify-end">
                <AppUiButtonSideSecondary>Eliminar</AppUiButtonSideSecondary>
                <AppUiButtonSidePrimary>Salvar</AppUiButtonSidePrimary>
              </div>
            </UForm>
          </AppLayoutWrapper>
        </template>
      </UModal>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
