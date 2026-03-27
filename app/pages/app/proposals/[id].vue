<script lang="ts" setup>
definePageMeta({ layout: "app" });

const tags = ref<string[]>(["python", "javascript", "java"]);
const proposalText = ref("");
const proposalValue = ref("");
</script>

<template>
  <div class="flex gap-8 items-start max-w-5xl mx-auto">
    <!-- Main Content (Job Posting) -->
    <div class="flex-1 min-w-0 space-y-6">
      <!-- Job Title Header -->
      <UCard>
        <div class="space-y-3">
          <div class="flex items-start justify-between gap-4">
            <h1 class="text-xl font-bold text-gray-900 dark:text-white leading-snug">
              Lorem ipsum, dolor sit amet consectetur adipisicing elit. Illo at,
              ratione totam fugiat omnis nobis iste placeat.
            </h1>
            <span
              class="text-xl font-bold text-primary-500 shrink-0 whitespace-nowrap"
            >
              500,000.00 Kz
            </span>
          </div>
          <div class="flex items-center gap-4 flex-wrap">
            <UiRating :value="5" />
            <span class="text-xs text-gray-400 dark:text-gray-500">
              Avaliações:
              <span class="font-medium text-gray-600 dark:text-gray-300">(5)</span>
            </span>
            <span class="text-xs text-gray-400 dark:text-gray-500">
              Postado em:
              <span class="font-medium text-gray-600 dark:text-gray-300">23/03/2026</span>
            </span>
            <UBadge color="success" variant="subtle" size="xs" icon="i-lucide-circle-dot">
              Aberto
            </UBadge>
          </div>
        </div>
      </UCard>

      <!-- Description Card -->
      <UCard>
        <template #header>
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-file-text" class="h-4 w-4 text-gray-500" />
            <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">
              Descrição do Projeto
            </span>
          </div>
        </template>

        <div class="space-y-5">
          <p class="text-sm text-gray-600 dark:text-gray-400 leading-relaxed text-justify">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
            ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
            voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
            ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
            voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
            ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
            voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
          </p>

          <USeparator />

          <!-- Details Grid -->
          <div class="grid grid-cols-3 gap-4">
            <div>
              <p class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide">
                Categoria
              </p>
              <p class="text-sm font-medium text-gray-900 dark:text-white mt-1">
                Desenvolvimento de Software
              </p>
            </div>
            <div>
              <p class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide">
                Subcategoria
              </p>
              <p class="text-sm font-medium text-gray-900 dark:text-white mt-1">
                Desenvolvimento Web
              </p>
            </div>
            <div>
              <p class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide">
                Prazo de entrega
              </p>
              <p class="text-sm font-medium text-gray-900 dark:text-white mt-1">
                30/03/2026
              </p>
            </div>
          </div>

          <!-- Skills -->
          <div>
            <p class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide mb-2">
              Habilidades necessárias
            </p>
            <div class="flex gap-2 flex-wrap">
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
          </div>
        </div>
      </UCard>

      <!-- Submit Proposal Form -->
      <UCard>
        <template #header>
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-send" class="h-4 w-4 text-gray-500" />
            <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">
              Enviar Proposta
            </span>
          </div>
        </template>

        <UForm class="space-y-4">
          <UFormField
            label="A sua proposta"
            name="proposal"
            hint="Descreva como irá abordar este projeto"
          >
            <UTextarea
              v-model="proposalText"
              :rows="5"
              class="w-full"
              placeholder="Escreva a sua proposta aqui..."
            />
          </UFormField>
          <div class="grid grid-cols-2 gap-4">
            <UFormField label="Valor proposto (Kz)" name="value">
              <UInput
                v-model="proposalValue"
                class="w-full"
                placeholder="500,000.00"
                icon="i-lucide-banknote"
              />
            </UFormField>
            <UFormField label="Prazo estimado" name="deadline">
              <UInputDate class="w-full" />
            </UFormField>
          </div>
          <div class="flex justify-end pt-1">
            <UButton
              type="submit"
              color="primary"
              variant="solid"
              icon="i-lucide-send"
              label="Enviar Proposta"
            />
          </div>
        </UForm>
      </UCard>
    </div>

    <!-- Sidebar: Client Info + Activity -->
    <aside class="w-64 shrink-0">
      <UCard class="sticky top-6">
        <div class="space-y-5">
          <!-- Client Info -->
          <div class="flex items-center gap-3">
            <div
              class="h-10 w-10 rounded-xl bg-blue-600 flex items-center justify-center text-sm font-bold text-white select-none shrink-0"
            >
              AA
            </div>
            <div>
              <p class="text-sm font-semibold text-gray-900 dark:text-white">
                Alessandro Almeida
              </p>
              <UiRating :value="5" />
            </div>
          </div>

          <USeparator />

          <div class="space-y-2">
            <p class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wide">
              Atividade
            </p>
            <div class="space-y-1.5">
              <div class="flex justify-between text-sm">
                <span class="text-gray-500 dark:text-gray-400">Propostas enviadas</span>
                <span class="font-semibold text-gray-900 dark:text-white">2</span>
              </div>
              <div class="flex justify-between text-sm">
                <span class="text-gray-500 dark:text-gray-400">Última proposta</span>
                <span class="font-semibold text-gray-900 dark:text-white">há 2h</span>
              </div>
            </div>
          </div>

          <USeparator />

          <div class="space-y-2">
            <p class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wide">
              Informação do Cliente
            </p>
            <div class="space-y-1.5">
              <div class="flex justify-between text-sm">
                <span class="text-gray-500 dark:text-gray-400">Propostas publicadas</span>
                <span class="font-semibold text-gray-900 dark:text-white">5</span>
              </div>
              <div class="flex justify-between text-sm">
                <span class="text-gray-500 dark:text-gray-400">Membro desde</span>
                <span class="font-semibold text-gray-900 dark:text-white">2023</span>
              </div>
            </div>
          </div>

          <UButton
            block
            size="sm"
            color="neutral"
            variant="ghost"
            icon="i-lucide-user"
            label="Ver perfil do cliente"
            to="/app/clients/1"
          />
        </div>
      </UCard>
    </aside>
  </div>
</template>
