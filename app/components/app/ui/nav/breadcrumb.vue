<script setup lang="ts">
const route = useRoute();

/** Mapeamento de segmentos de rota para labels em português */
const labelMap: Record<string, string> = {
  app: "Início",
  proposals: "Propostas",
  clients: "Clientes",
  freelancers: "Freelancers",
  notifications: "Notificações",
  account: "Conta",
  settings: "Definições",
  profile: "Perfil",
  freelancer: "Freelancer",
  client: "Cliente",
  projects: "Projetos",
  experience: "Experiência",
  skills: "Competências",
  reviews: "Avaliações",
};

const iconMap: Record<string, string> = {
  app: "i-lucide-home",
  proposals: "i-lucide-file-text",
  clients: "i-lucide-building-2",
  freelancers: "i-lucide-users",
  notifications: "i-lucide-bell",
  account: "i-lucide-circle-user",
  settings: "i-lucide-settings",
  profile: "i-lucide-id-card",
  freelancer: "i-lucide-briefcase",
  client: "i-lucide-building-2",
  projects: "i-lucide-folder-open",
  experience: "i-lucide-graduation-cap",
  skills: "i-lucide-star",
  reviews: "i-lucide-message-square",
};

const breadcrumbs = computed(() => {
  const segments = route.path.split("/").filter(Boolean);
  let path = "";

  return segments.map((seg, i) => {
    path += `/${seg}`;
    const isLast = i === segments.length - 1;
    const isDynamic = /^\d+$/.test(seg);
    const label = isDynamic ? `#${seg}` : (labelMap[seg] ?? seg);
    const icon = !isDynamic ? iconMap[seg] : "i-lucide-hash";

    return {
      label,
      icon,
      ...(isLast ? {} : { to: path }),
    };
  });
});
</script>

<template>
  <nav aria-label="breadcrumb">
    <UBreadcrumb :items="breadcrumbs" />
  </nav>
</template>
