<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutWrapper>
    <div class="w-full mx-auto py-10 px-4 space-y-6">
      <!-- Cabeçalho da página -->
      <div>
        <h1 class="text-xl font-bold text-gray-900 dark:text-white">
          Minha Conta
        </h1>
        <p class="text-sm text-gray-500 dark:text-gray-400 mt-1">
          Informações gerais da tua conta na plataforma.
        </p>
      </div>

      <!-- Card: Identidade -->
      <UCard>
        <template #header>
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-circle-user" class="h-4 w-4 text-gray-500" />
            <span
              class="text-sm font-semibold text-gray-700 dark:text-gray-300"
            >
              Informações pessoais
            </span>
          </div>
        </template>

        <div class="flex items-center gap-4 mb-6">
          <div
            class="h-16 w-16 rounded-xl bg-violet-600 flex items-center justify-center text-xl font-bold text-white select-none shrink-0"
          >
            AA
          </div>
          <div>
            <p class="text-lg font-bold text-gray-900 dark:text-white">
              Alessandro Almeida
            </p>
            <p class="text-sm text-gray-500 dark:text-gray-400">
              Membro desde Janeiro de 2023
            </p>
          </div>
        </div>

        <div class="divide-y divide-gray-100 dark:divide-gray-800">
          <!-- Primeiro nome -->
          <div class="flex items-center justify-between py-3">
            <div>
              <p
                class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                Primeiro nome
              </p>
              <p
                class="text-sm font-medium text-gray-900 dark:text-white mt-0.5"
              >
                Alessandro
              </p>
            </div>
            <UButton
              size="xs"
              color="neutral"
              variant="ghost"
              icon="i-lucide-pencil"
              label="Editar"
              to="/settings/account"
            />
          </div>

          <!-- Último nome -->
          <div class="flex items-center justify-between py-3">
            <div>
              <p
                class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                Último nome
              </p>
              <p
                class="text-sm font-medium text-gray-900 dark:text-white mt-0.5"
              >
                Almeida
              </p>
            </div>
            <UButton
              size="xs"
              color="neutral"
              variant="ghost"
              icon="i-lucide-pencil"
              label="Editar"
              to="/settings/account"
            />
          </div>

          <!-- Email -->
          <div class="flex items-center justify-between py-3">
            <div>
              <p
                class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                Email
              </p>
              <div class="flex items-center gap-2 mt-0.5">
                <p class="text-sm font-medium text-gray-900 dark:text-white">
                  alessandro.almeida@email.com
                </p>
                <UBadge color="success" variant="subtle" size="xs"
                  >Verificado</UBadge
                >
              </div>
            </div>
            <UButton
              size="xs"
              color="neutral"
              variant="ghost"
              icon="i-lucide-pencil"
              label="Editar"
              to="/settings/account"
            />
          </div>
        </div>
      </UCard>

      <!-- Card: Detalhes da conta -->
      <UCard>
        <template #header>
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-shield" class="h-4 w-4 text-gray-500" />
            <span class="text-sm font-semibold text-gray-700 dark:text-gray-300"
              >Detalhes da conta</span
            >
          </div>
        </template>

        <div class="divide-y divide-gray-100 dark:divide-gray-800">
          <!-- Membro desde -->
          <div class="flex items-center justify-between py-3">
            <div>
              <p
                class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                Membro desde
              </p>
              <p
                class="text-sm font-medium text-gray-900 dark:text-white mt-0.5"
              >
                15 de Janeiro de 2023
              </p>
            </div>
            <UIcon name="i-lucide-calendar" class="h-4 w-4 text-gray-400" />
          </div>

          <!-- Tipo de conta -->
          <div class="flex items-center justify-between py-3">
            <div>
              <p
                class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                Tipo de conta
              </p>
              <div class="flex items-center gap-2 mt-0.5">
                <UBadge
                  color="primary"
                  variant="subtle"
                  size="sm"
                  icon="i-lucide-building-2"
                  >Cliente</UBadge
                >
                <UBadge
                  color="success"
                  variant="subtle"
                  size="sm"
                  icon="i-lucide-briefcase"
                  >Freelancer</UBadge
                >
              </div>
            </div>
            <UIcon name="i-lucide-layers" class="h-4 w-4 text-gray-400" />
          </div>

          <!-- Estado da conta -->
          <div class="flex items-center justify-between py-3">
            <div>
              <p
                class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
              >
                Estado da conta
              </p>
              <div class="flex items-center gap-1.5 mt-0.5">
                <span
                  class="h-2 w-2 rounded-full bg-green-500 inline-block"
                ></span>
                <p class="text-sm font-medium text-gray-900 dark:text-white">
                  Ativa
                </p>
              </div>
            </div>
            <UIcon
              name="i-lucide-check-circle"
              class="h-4 w-4 text-green-500"
            />
          </div>
        </div>
      </UCard>

      <!-- Card: Perfil Freelancer -->
      <UCard>
        <template #header>
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-briefcase" class="h-4 w-4 text-gray-500" />
            <span
              class="text-sm font-semibold text-gray-700 dark:text-gray-300"
            >
              Perfil Freelancer
            </span>
          </div>
        </template>

        <div class="flex items-start justify-between gap-4">
          <div class="space-y-1">
            <p class="text-sm font-medium text-gray-900 dark:text-white">
              Desenvolvedor Backend
            </p>
            <p class="text-xs text-gray-500 dark:text-gray-400">
              O teu perfil público como freelancer está ativo e visível para
              clientes na plataforma.
            </p>
            <div class="flex items-center gap-3 pt-1">
              <span
                class="flex items-center gap-1 text-xs text-gray-500 dark:text-gray-400"
              >
                <UIcon
                  name="i-lucide-star"
                  class="h-3.5 w-3.5 text-yellow-400"
                />
                3.8 · 24 avaliações
              </span>
              <span
                class="flex items-center gap-1 text-xs text-gray-500 dark:text-gray-400"
              >
                <UIcon name="i-lucide-folder-check" class="h-3.5 w-3.5" />
                12 projetos
              </span>
              <span
                class="flex items-center gap-1 text-xs text-gray-500 dark:text-gray-400"
              >
                <UIcon name="i-lucide-clock" class="h-3.5 w-3.5" />
                €35/h
              </span>
            </div>
          </div>
          <UButton
            size="xs"
            color="neutral"
            variant="outline"
            label="Ver perfil"
            to="/app/profile/freelancer"
            icon="i-lucide-arrow-up-right"
            trailing
          />
        </div>
      </UCard>

      <!-- Rodapé: link para definições -->
      <div class="flex items-center justify-between pt-2">
        <p class="text-xs text-gray-400 dark:text-gray-500">
          Para alterar email, password ou preferências, vai às definições.
        </p>
        <UButton
          size="sm"
          color="neutral"
          variant="outline"
          icon="i-lucide-settings"
          label="Definições"
          to="/app/account/settings"
        />
      </div>
    </div>
  </AppLayoutWrapper>
</template>
