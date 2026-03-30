<script lang="ts" setup>
import type { DropdownMenuItem, NavigationMenuItem } from "@nuxt/ui";

const route = useRoute();

const dropdownItems = computed(() => [
  [
    {
      label: "Perfil de freelancer",
      to: "/app/profile/freelancer",
    },
    {
      label: "Perfil de cliente",
      to: "/app/profile/client",
    },
  ],
  [
    {
      label: "Configurações",
      to: "/app/settings",
    },
    {
      label: "Notificações",
    },
  ],
  {
    label: "Sair",
    to: "/logout",
  },
]);

const items = computed<NavigationMenuItem[]>(() => [
  {
    label: "Encontrar trabalho",
    to: "/app/proposals",
    active: route.path.startsWith("/app/proposals"),
  },
  {
    label: "Freelancers",
    to: "/app/freelancers",
    active: route.path.startsWith("/app/freelancers"),
  },
  {
    label: "Clientes",
    to: "/app/clients",
    active: route.path.startsWith("/app/clients"),
  },
]);
</script>

<template>
  <UHeader>
    <template #title>
      <UiLogo size="md" />
    </template>
    <UNavigationMenu :items="items" class="gap-4 flex" />
    <template #right>
      <div class="flex gap-4 items-center-safe justify-center">
        <AppUiButtonNotifications />
        <AppUiButtonAccount />
      </div>
    </template>
  </UHeader>
  <!-- <header class="bg-slate-800 px-20 h-17 flex items-center"> -->
  <!-- <UiLogo size="md" />
    <nav class="ml-10 h-full">
      <ul class="flex items-center space-x-6 h-full">
        <li>
          <AppUiLinkNav to="/app/proposals"> Propostas </AppUiLinkNav>
        </li>
        <li>
          <AppUiLinkNav to="/app/freelancers">Freelancers</AppUiLinkNav>
        </li>
      </ul>
    </nav>

    <div
      class="ml-auto bg-slate-900 px-2 py-1.5 space-x-2 flex items-center rounded-full mr-6"
    >
      <label for="search" class="flex items-center">
        <Icon
          name="mingcute:search-line"
          class="text-xl text-slate-600 font-semibold"
        />
      </label>
      <input
        type="search"
        placeholder="pesquisar..."
        name="search"
        id="search"
        class="outline-0"
      />
    </div>
    <ul class="flex gap-4 items-center-safe justify-center">
      <li class="flex items-center">
        <AppUiButtonNotifications />
      </li>
      <li>
        <AppUiButtonAccount />
      </li>
    </ul> -->
  <!-- </header> -->
</template>
