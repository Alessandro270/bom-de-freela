<script lang="ts" setup>
import type { NavigationMenuItem } from "@nuxt/ui";

const items = computed<NavigationMenuItem[]>(() => [
  { label: "Encontrar Propostas", to: "/app/proposals/" },
  { label: "Encontrar Freelancers", to: "/app/proposals/" },
]);
</script>

<template>
  <UHeader>
    <template #left>
      <div class="space-x-10 flex">
        <UiLogo />

        <UNavigationMenu :items="items" variant="link" />
      </div>
    </template>

    <template #right>
      <div class="flex space-x-4">
        <UButton
          label="Entrar"
          color="neutral"
          variant="link"
          to="/auth/login"
        />
        <UButton label="Cadastrar" color="primary" to="/auth/sign-up" />
      </div>
    </template>
  </UHeader>
</template>
