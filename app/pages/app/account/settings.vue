<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutWrapper>
    <div class="w-full mx-auto py-10 px-4 space-y-6">
      <!-- Cabeçalho da página -->
      <div>
        <h1 class="text-xl font-bold text-gray-900 dark:text-white">
          Definições
        </h1>
        <p class="text-sm text-gray-500 dark:text-gray-400 mt-1">
          Edita as informações da tua conta.
        </p>
      </div>

      <!-- Card: Informações pessoais -->
      <UCard>
        <template #header>
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-circle-user" class="h-4 w-4 text-gray-500" />
            <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">
              Informações pessoais
            </span>
          </div>
        </template>

        <form class="space-y-4">
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <!-- Primeiro nome -->
            <UFormField label="Primeiro nome" name="firstName">
              <UInput
                placeholder="Alessandro"
                value="Alessandro"
                class="w-full"
              />
            </UFormField>

            <!-- Último nome -->
            <UFormField label="Último nome" name="lastName">
              <UInput
                placeholder="Almeida"
                value="Almeida"
                class="w-full"
              />
            </UFormField>
          </div>

          <!-- Email -->
          <UFormField label="Email" name="email">
            <UInput
              placeholder="exemplo@email.com"
              value="alessandro.almeida@email.com"
              type="email"
              class="w-full"
            />
          </UFormField>

          <div class="flex justify-end pt-2">
            <UButton
              size="sm"
              color="primary"
              variant="solid"
              icon="i-lucide-save"
              label="Guardar alterações"
            />
          </div>
        </form>
      </UCard>

      <!-- Card: Alterar password -->
      <UCard>
        <template #header>
          <div class="flex items-center gap-2">
            <UIcon name="i-lucide-lock" class="h-4 w-4 text-gray-500" />
            <span class="text-sm font-semibold text-gray-700 dark:text-gray-300">
              Alterar password
            </span>
          </div>
        </template>

        <form class="space-y-4">
          <!-- Password atual -->
          <UFormField label="Password atual" name="currentPassword">
            <UInput
              placeholder="••••••••"
              type="password"
              class="w-full"
            />
          </UFormField>

          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <!-- Nova password -->
            <UFormField label="Nova password" name="newPassword">
              <UInput
                placeholder="••••••••"
                type="password"
                class="w-full"
              />
            </UFormField>

            <!-- Confirmar nova password -->
            <UFormField label="Confirmar nova password" name="confirmPassword">
              <UInput
                placeholder="••••••••"
                type="password"
                class="w-full"
              />
            </UFormField>
          </div>

          <div class="flex justify-end pt-2">
            <UButton
              size="sm"
              color="primary"
              variant="solid"
              icon="i-lucide-save"
              label="Atualizar password"
            />
          </div>
        </form>
      </UCard>

      <!-- Rodapé: link para informações da conta -->
      <div class="flex items-center justify-between pt-2">
        <p class="text-xs text-gray-400 dark:text-gray-500">
          Para consultar os detalhes gerais da conta, vai às informações.
        </p>
        <UButton
          size="sm"
          color="neutral"
          variant="outline"
          icon="i-lucide-circle-user"
          label="Minha conta"
          to="/app/account"
        />
      </div>
    </div>
  </AppLayoutWrapper>
</template>
