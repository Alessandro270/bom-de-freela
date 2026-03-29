<script lang="ts" setup>
import type { NavigationMenuItem } from "@nuxt/ui";

const route = useRoute();

const navGroups = computed<NavigationMenuItem[][]>(() => [
  [
    {
      label: "Visão Geral",
      icon: "i-lucide-layout-dashboard",
      to: "/admin",
      active: route.path === "/admin",
    },
  ],
  [
    {
      label: "Usuários",
      type: "label",
    },
    {
      label: "Contas",
      icon: "i-lucide-users",
      to: "/admin/accounts",
    },
    {
      label: "Clientes",
      icon: "i-lucide-building-2",
      to: "/admin/clients",
    },
    {
      label: "Freelancers",
      icon: "i-lucide-user-check",
      to: "/admin/freelancers",
    },
  ],
  [
    {
      label: "Conteúdo",
      type: "label",
    },
    {
      label: "Projetos",
      icon: "i-lucide-folder-open",
      to: "/admin/projects",
    },
    {
      label: "Propostas",
      icon: "i-lucide-file-text",
      to: "/admin/proposals",
    },
  ],
  [
    {
      label: "Financeiro",
      type: "label",
    },
    {
      label: "Comprovativos",
      icon: "i-lucide-receipt",
      to: "/admin/bills",
    },
  ],
]);
</script>

<template>
  <UNavigationMenu
    :items="navGroups"
    orientation="vertical"
    class="w-full data-[orientation=vertical]:w-full"
  />
</template>
