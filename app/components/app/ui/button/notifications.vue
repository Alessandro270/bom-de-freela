<script setup lang="ts">
type NotificationType =
  | "contract_invite"
  | "proposal"
  | "payment"
  | "review"
  | "message";

interface Notification {
  id: number;
  type: NotificationType;
  title: string;
  body: string;
  time: string;
  read: boolean;
}

const notifications = ref<Notification[]>([
  {
    id: 1,
    type: "contract_invite",
    title: "Convite de contrato recebido",
    body: 'Maria Santos convidou-te para "Redesign de App Móvel".',
    time: "há 10 min",
    read: false,
  },
  {
    id: 2,
    type: "proposal",
    title: "Nova proposta recebida",
    body: 'João Silva enviou uma proposta para "Website E-commerce".',
    time: "há 35 min",
    read: false,
  },
  {
    id: 3,
    type: "payment",
    title: "Pagamento confirmado",
    body: "O pagamento de 850.000 Kz foi processado com sucesso.",
    time: "há 2 h",
    read: false,
  },
  {
    id: 4,
    type: "message",
    title: "Mensagem de Carlos Ferreira",
    body: "Podemos agendar uma reunião para amanhã às 10h?",
    time: "ontem",
    read: true,
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

function clearAll() {
  notifications.value = [];
}

const iconByType: Record<NotificationType, string> = {
  contract_invite: "i-lucide-file-signature",
  proposal: "i-lucide-send",
  payment: "i-lucide-circle-dollar-sign",
  review: "i-lucide-refresh-ccw",
  message: "i-lucide-message-circle",
};

const colorByType: Record<NotificationType, string> = {
  contract_invite: "text-green-500",
  proposal: "text-green-500",
  payment: "text-green-500",
  review: "text-green-500",
  message: "text-green-500",
};

const bgByType: Record<NotificationType, string> = {
  contract_invite: "bg-green-100 dark:bg-green-950/50",
  proposal: "bg-green-100 dark:bg-green-950/50",
  payment: "bg-green-100 dark:bg-green-950/50",
  review: "bg-green-100 dark:bg-green-950/50",
  message: "bg-green-100 dark:bg-green-950/50",
};
</script>

<template>
  <UPopover
    :content="{ align: 'end', side: 'bottom' }"
    :ui="{ content: 'p-0 w-96' }"
  >
    <!-- Trigger Button -->
    <UButton
      icon="i-lucide-bell"
      color="neutral"
      variant="ghost"
      aria-label="Notificações"
      class="relative"
    >
      <template #trailing>
        <span
          v-if="unreadCount > 0"
          class="absolute -top-1 -right-1 flex h-4 w-4 items-center justify-center rounded-full bg-red-500 text-[10px] font-bold text-white leading-none pointer-events-none"
        >
          {{ unreadCount > 9 ? "9+" : unreadCount }}
        </span>
      </template>
    </UButton>

    <!-- Popover Content -->
    <template #content>
      <!-- Header -->
      <div
        class="flex items-center justify-between px-4 py-3 border-b border-gray-100 dark:border-gray-800"
      >
        <div class="flex items-center gap-2">
          <p class="text-sm font-semibold text-gray-900 dark:text-white">
            Notificações
          </p>
          <UBadge
            v-if="unreadCount > 0"
            color="error"
            variant="solid"
            size="xs"
          >
            {{ unreadCount }}
          </UBadge>
        </div>
        <div class="flex items-center gap-1">
          <UButton
            v-if="unreadCount > 0"
            size="xs"
            color="neutral"
            variant="ghost"
            icon="i-lucide-check-check"
            label="Marcar todas"
            @click="markAllAsRead"
          />
          <UButton
            v-if="notifications.length > 0"
            size="xs"
            color="error"
            variant="ghost"
            icon="i-lucide-trash-2"
            @click="clearAll"
          />
        </div>
      </div>

      <!-- Empty state -->
      <div
        v-if="notifications.length === 0"
        class="flex flex-col items-center justify-center py-10 px-4 text-center"
      >
        <UIcon
          name="i-lucide-bell-off"
          class="h-8 w-8 text-gray-300 dark:text-gray-600 mb-2"
        />
        <p class="text-sm text-gray-400 dark:text-gray-500">Sem notificações</p>
      </div>

      <!-- Notifications List -->
      <div
        v-else
        class="divide-y divide-gray-100 dark:divide-gray-800 max-h-96 overflow-y-auto"
      >
        <div
          v-for="notif in notifications"
          :key="notif.id"
          class="px-4 py-3 transition-colors hover:bg-gray-50 dark:hover:bg-gray-900/50"
          :class="!notif.read ? 'bg-primary-50/40 dark:bg-primary-950/20' : ''"
        >
          <div class="flex items-start gap-3">
            <!-- Icon -->
            <div
              class="h-8 w-8 rounded-full flex items-center justify-center shrink-0 mt-0.5"
              :class="bgByType[notif.type]"
            >
              <UIcon
                :name="iconByType[notif.type]"
                class="h-4 w-4"
                :class="colorByType[notif.type]"
              />
            </div>

            <!-- Content -->
            <div class="flex-1 min-w-0">
              <div class="flex items-start justify-between gap-1">
                <p
                  class="text-xs font-semibold text-gray-900 dark:text-white leading-snug"
                >
                  {{ notif.title }}
                </p>
                <span
                  v-if="!notif.read"
                  class="h-2 w-2 rounded-full bg-primary-500 shrink-0 mt-1"
                />
              </div>
              <p
                class="text-xs text-gray-500 dark:text-gray-400 mt-0.5 leading-snug line-clamp-2"
              >
                {{ notif.body }}
              </p>
              <div class="flex items-center justify-between mt-1.5">
                <span class="text-[11px] text-gray-400 dark:text-gray-600">
                  {{ notif.time }}
                </span>
                <UButton
                  v-if="!notif.read"
                  size="xs"
                  color="neutral"
                  variant="ghost"
                  icon="i-lucide-check"
                  label="Lida"
                  class="h-5 text-[11px]"
                  @click="markAsRead(notif.id)"
                />
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Footer -->
      <div class="px-4 py-2.5 border-t border-gray-100 dark:border-gray-800">
        <UButton
          size="xs"
          color="primary"
          variant="ghost"
          icon="i-lucide-arrow-right"
          label="Ver todas as notificações"
          trailing
          to="/app/notifications"
          class="w-full justify-center"
        />
      </div>
    </template>
  </UPopover>
</template>
