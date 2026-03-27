<script setup lang="ts">
import type { DropdownMenuItem } from "@nuxt/ui";

const user = ref({
  name: "Alessandro Almeida",
  email: "alessandro.almeida@gmail.com",
  avatar: "",
});

const userInitials = computed(() =>
  user.value.name
    .split(" ")
    .map((n) => n[0])
    .slice(0, 2)
    .join("")
    .toUpperCase(),
);

const activeAccount = ref<"personal" | "freelancer" | "client">("personal");

function switchAccount(type: typeof activeAccount.value) {
  activeAccount.value = type;
}

function logout() {
  // ex: await useAuth().logout()
  navigateTo("/login");
}

const items = computed<DropdownMenuItem[][]>(() => [
  // Label do utilizador
  [
    {
      label: user.value.name,
      avatar: user.value.avatar ? { src: user.value.avatar } : undefined,
      type: "label" as const,
    },
  ],

  // Trocar tipo de conta
  [
    {
      label: "Perfil de Freelancer",
      icon: "i-lucide-briefcase",
      to: "/app/profile/freelancer",
    },
    {
      label: "Perfil de Cliente",
      icon: "i-lucide-building-2",
      to: "/app/profile/client",
    },
  ],

  // Perfil e configurações
  [
    {
      label: "O meu perfil",
      icon: "i-lucide-circle-user",
      to: "/profile",
    },
    {
      label: "Definições",
      icon: "i-lucide-settings",
      to: "/settings",
      kbds: [","],
    },
    {
      label: "Faturação",
      icon: "i-lucide-credit-card",
      to: "/billing",
    },
  ],

  // Suporte
  [
    {
      label: "Ajuda & Suporte",
      icon: "i-lucide-life-buoy",
      to: "/support",
    },
    {
      label: "Documentação",
      icon: "i-lucide-book-open",
      to: "https://docs.exemplo.com",
      target: "_blank",
    },
  ],

  // Logout
  [
    {
      label: "Terminar sessão",
      icon: "i-lucide-log-out",
      color: "error" as const,
      kbds: ["shift", "meta", "q"],
      onSelect: logout,
    },
  ],
]);
</script>

<template>
  <UDropdownMenu :items="items">
    <button
      class="flex h-8 w-8 items-center justify-center rounded-full bg-violet-500 text-xs font-bold text-white ring-2 ring-transparent hover:ring-violet-300 dark:hover:ring-violet-700 transition-all focus:outline-none focus:ring-2 focus:ring-violet-400"
      aria-label="Menu da conta"
    >
      <img
        v-if="user.avatar"
        :src="user.avatar"
        :alt="user.name"
        class="h-full w-full rounded-full object-cover"
      />
      <span v-else>{{ userInitials }}</span>
    </button>
  </UDropdownMenu>
</template>
