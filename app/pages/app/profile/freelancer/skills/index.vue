<script lang="ts" setup>
definePageMeta({ layout: "app" });

const skills = reactive([
  { id: 1, name: "Python", value: 4 },
  { id: 2, name: "JavaScript", value: 5 },
  { id: 3, name: "CSS", value: 4 },
  { id: 4, name: "HTML", value: 5 },
]);
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileFreelancer>
      <!-- Cabeçalho da secção -->
      <div class="flex items-center justify-between mb-4">
        <div class="flex items-center gap-2">
          <h2 class="text-sm font-semibold text-gray-700 dark:text-gray-300 uppercase tracking-wide">
            Habilidades
          </h2>
          <UBadge color="neutral" variant="subtle" size="xs">
            {{ skills.length }}
          </UBadge>
        </div>
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
              <UIcon name="i-lucide-star" class="h-4 w-4 text-gray-500" />
              <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">
                Editar habilidades
              </span>
            </div>
          </template>
          <template #body>
            <UForm class="space-y-5">
              <UFormField
                v-for="skill in skills"
                :key="skill.id"
                :label="skill.name"
                orientation="horizontal"
              >
                <AppUiButtonRating :rating="skill.value" />
              </UFormField>
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

      <!-- Lista de habilidades -->
      <ul class="divide-y divide-gray-100 dark:divide-gray-800">
        <AppUiCardSkill
          v-for="skill in skills"
          :key="skill.id"
          :value="skill.value"
        >
          {{ skill.name }}
        </AppUiCardSkill>
      </ul>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
