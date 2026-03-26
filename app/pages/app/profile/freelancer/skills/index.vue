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
        <div class="w-full flex justify-end">
          <UButton label="Editar" color="neutral" variant="outline" />
        </div>
        <template #header>
          <AppUiHeaderProfile>Editar habilidades</AppUiHeaderProfile>
        </template>
        <template #body>
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
              <AppUiButtonSidePrimary type="submit">
                Salvar
              </AppUiButtonSidePrimary>
            </div>
          </UForm>
        </template>
      </UModal>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
