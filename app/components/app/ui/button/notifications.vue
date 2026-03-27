<script setup lang="ts">
import type { DropdownMenuItem } from "@nuxt/ui";

interface Notification {
  id: number;
  title: string;
  body: string;
  time: string;
  read: boolean;
  iconColor: string;
}

const notifications = ref<Notification[]>([
  {
    id: 1,
    title: "Nova proposta recebida",
    body: 'João Silva enviou uma proposta para "Website E-commerce".',
    time: "há 5 min",
    read: false,
    iconColor: "text-blue-500",
  },
  {
    id: 2,
    title: "Pagamento confirmado",
    body: "O pagamento de €850,00 foi processado com sucesso.",
    time: "há 1 h",
    read: false,
    iconColor: "text-green-500",
  },
  {
    id: 3,
    title: "Revisão solicitada",
    body: 'O cliente pediu revisão em "Design UI – Sprint 2".',
    time: "há 3 h",
    read: false,
    iconColor: "text-amber-500",
  },
  {
    id: 4,
    title: "Mensagem de Maria Santos",
    body: "Podemos agendar uma reunião para amanhã às 10h?",
    time: "ontem",
    read: true,
    iconColor: "text-violet-500",
  },
]);

const unreadCount = computed(
  () => notifications.value.filter((n) => !n.read).length,
);

function markAsRead(id: number) {
  const n = notifications.value.find((n) => n.id === id);
  if (n) n.read = true;
}

function markAllAsRead() {
  notifications.value.forEach((n) => (n.read = true));
}

function removeNotification(id: number) {
  notifications.value = notifications.value.filter((n) => n.id !== id);
}

function clearAll() {
  notifications.value = [];
}

// Constrói os items do dropdown a partir das notificações
const items = computed<DropdownMenuItem[][]>(() => {
  if (notifications.value.length === 0) {
    return [
      [
        {
          label: "Sem notificações",
          icon: "i-lucide-bell-off",
          disabled: true,
          type: "label" as const,
        },
      ],
    ];
  }

  const notifItems: DropdownMenuItem[] = notifications.value.map((n) => ({
    label: n.title,
    // Descrição debaixo do label via slot não é suportada em items,
    // usamos o badge para mostrar o tempo e a classe para o estado lido
    badge: n.time,
    class: n.read ? "opacity-60" : "",
    onSelect: () => markAsRead(n.id),
  }));

  const actions: DropdownMenuItem[] = [];

  if (unreadCount.value > 0) {
    actions.push({
      label: "Marcar todas como lidas",
      icon: "i-lucide-check-check",
      onSelect: markAllAsRead,
    });
  }

  actions.push({
    label: "Limpar todas",
    icon: "i-lucide-trash-2",
    color: "error" as const,
    onSelect: clearAll,
  });

  return [notifItems, actions];
});
</script>

<template>
  <UDropdownMenu :items="items">
    <UButton
      icon="i-lucide-bell"
      color="neutral"
      variant="ghost"
      aria-label="Notificações"
      class="relative"
    >
      <!-- Badge de não lidas sobreposta ao botão -->
      <template #trailing>
        <span
          v-if="unreadCount > 0"
          class="absolute -top-1 -right-1 flex h-4 w-4 items-center justify-center rounded-full bg-red-500 text-[10px] font-bold text-white leading-none pointer-events-none"
        >
          {{ unreadCount > 9 ? "9+" : unreadCount }}
        </span>
      </template>
    </UButton>
  </UDropdownMenu>
</template>
