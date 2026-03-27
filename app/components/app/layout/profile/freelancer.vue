<script lang="ts" setup>
const tags = ref<string[]>(["Python", "Backend", "Pwa"]);
</script>

<template>
  <div class="space-y-4 w-full">
    <!-- Hero card: avatar + nome + rating + habilidades -->
    <UCard>
      <div class="flex flex-col gap-4">
        <!-- Linha principal: avatar + info + meta -->
        <div class="flex items-start justify-between gap-6">
          <!-- Avatar + nome + rating -->
          <div class="flex items-center gap-6">
            <div
              class="h-20 w-20 rounded-xl bg-violet-600 flex items-center justify-center text-2xl font-bold text-white select-none shrink-0"
            >
              AA
            </div>
            <div class="space-y-1">
              <h1 class="text-2xl font-bold text-gray-900 dark:text-white">
                Alessandro Almeida
              </h1>
              <p class="text-base font-medium text-gray-500 dark:text-gray-400">
                Desenvolvedor backend
              </p>
              <div class="flex items-center gap-1.5">
                <UiRating :value="4" />
                <span class="text-xs text-gray-400 dark:text-gray-500"
                  >(24 avaliações)</span
                >
              </div>
            </div>
          </div>

          <!-- Meta: membro desde + link público -->
          <div class="flex flex-col items-end gap-3 shrink-0">
            <div class="text-right">
              <p
                class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                Membro desde
              </p>
              <p class="text-sm font-semibold text-gray-900 dark:text-white">
                2023
              </p>
            </div>
            <UButton
              size="xs"
              color="neutral"
              variant="outline"
              label="Ver perfil público"
              icon="i-lucide-arrow-up-right"
              trailing
              to="/app/freelancers/1/"
            />
          </div>
        </div>

        <USeparator />

        <!-- Habilidades principais -->
        <div class="flex items-center justify-between gap-4">
          <div class="flex items-center gap-2 flex-wrap">
            <span
              class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide shrink-0"
            >
              Habilidades:
            </span>
            <UBadge
              v-for="tag in tags"
              :key="tag"
              color="primary"
              variant="subtle"
              size="sm"
            >
              {{ tag }}
            </UBadge>
          </div>

          <!-- Modal editar habilidades -->
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
                <UIcon name="i-lucide-tag" class="h-4 w-4 text-gray-500" />
                <span
                  class="text-sm font-semibold text-gray-700 dark:text-gray-300"
                >
                  Editar informações
                </span>
              </div>
            </template>
            <template #body>
              <UForm class="space-y-4">
                <UFormField label="Cargo">
                  <UInput class="w-full" />
                </UFormField>
                <UFormField label="Habilidades">
                  <UInputTags v-model="tags" class="w-full" />
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
      </div>
    </UCard>

    <!-- Navegação entre secções -->
    <AppUiNavBar
      :items="[
        { to: '/app/profile/freelancer/', label: 'Sobre mim' },
        { to: '/app/profile/freelancer/projects', label: 'Projetos' },
        { to: '/app/profile/freelancer/reviews', label: 'Avaliações' },
        { to: '/app/profile/freelancer/proposals', label: 'Propostas' },
        { to: '/app/profile/freelancer/skills', label: 'Habilidades' },
        { to: '/app/profile/freelancer/experience', label: 'Experiência' },
      ]"
    />

    <!-- Conteúdo da secção activa -->
    <UCard>
      <slot />
    </UCard>
  </div>
</template>
