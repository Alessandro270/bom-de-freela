<script lang="ts" setup>
definePageMeta({ layout: "app" });

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
  from?: string;
  projectTitle?: string;
  amount?: string;
}

const activeTab = ref<"all" | "unread">("all");

const notifications = ref<Notification[]>([
  {
    id: 1,
    type: "contract_invite",
    title: "Convite de contrato recebido",
    body: 'Maria Santos convidou-te para colaborar no projeto "Redesign de App Móvel". Revê os detalhes antes de aceitar.',
    time: "há 10 min",
    read: false,
    from: "Maria Santos",
    projectTitle: "Redesign de App Móvel",
  },
  {
    id: 2,
    type: "proposal",
    title: "Nova proposta recebida",
    body: 'João Silva enviou uma proposta para o projeto "Website E-commerce" com um orçamento de 450.000 Kz.',
    time: "há 35 min",
    read: false,
    from: "João Silva",
    projectTitle: "Website E-commerce",
  },
  {
    id: 3,
    type: "contract_invite",
    title: "Convite de contrato recebido",
    body: 'TechCorp Angola convidou-te para colaborar no projeto "Sistema de Gestão de Stocks". O prazo de resposta é de 48 horas.',
    time: "há 2 h",
    read: false,
    from: "TechCorp Angola",
    projectTitle: "Sistema de Gestão de Stocks",
  },
  {
    id: 4,
    type: "payment",
    title: "Pagamento confirmado",
    body: 'O pagamento de 850.000 Kz referente ao projeto "Dashboard Administrativo" foi processado e creditado na tua conta.',
    time: "há 4 h",
    read: false,
    projectTitle: "Dashboard Administrativo",
    amount: "850.000 Kz",
  },
  {
    id: 5,
    type: "review",
    title: "Revisão solicitada",
    body: 'O cliente pediu uma revisão na entrega "Design UI – Sprint 2". Tens 48 horas para submeter as alterações pedidas.',
    time: "ontem",
    read: true,
    projectTitle: "Design UI – Sprint 2",
  },
  {
    id: 6,
    type: "message",
    title: "Nova mensagem de Carlos Ferreira",
    body: "Olá! Podemos agendar uma reunião para amanhã às 10h para discutirmos os requisitos do novo módulo?",
    time: "ontem",
    read: true,
    from: "Carlos Ferreira",
  },
  {
    id: 7,
    type: "proposal",
    title: "Proposta aprovada",
    body: 'A tua proposta para o projeto "Plataforma de E-learning" foi aprovada pelo cliente. Verifica o contrato.',
    time: "há 2 dias",
    read: true,
    projectTitle: "Plataforma de E-learning",
  },
]);

const filteredNotifications = computed(() => {
  if (activeTab.value === "unread") {
    return notifications.value.filter((n) => !n.read);
  }
  return notifications.value;
});

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
  review: "bg-amber-100 dark:bg-amber-950/50",
  message: "bg-pink-100 dark:bg-pink-950/50",
};

const labelByType: Record<NotificationType, string> = {
  contract_invite: "Contrato",
  proposal: "Proposta",
  payment: "Pagamento",
  review: "Revisão",
  message: "Mensagem",
};

const badgeColorByType: Record<
  NotificationType,
  "primary" | "success" | "warning" | "error" | "info" | "neutral"
> = {
  contract_invite: "primary",
  proposal: "primary",
  payment: "primary",
  review: "primary",
  message: "primary",
};
</script>

<template>
  <AppLayoutWrapper>
    <div class="w-full py-8 px-4 space-y-6">
      <!-- Page Header -->
      <div class="flex items-start justify-between gap-4 flex-wrap">
        <div>
          <div class="flex items-center gap-2.5">
            <h1 class="text-xl font-bold text-gray-900 dark:text-white">
              Notificações
            </h1>
            <UBadge
              v-if="unreadCount > 0"
              color="error"
              variant="solid"
              size="xs"
            >
              {{ unreadCount }} não {{ unreadCount === 1 ? "lida" : "lidas" }}
            </UBadge>
          </div>
          <p class="text-sm text-gray-500 dark:text-gray-400 mt-1">
            Acompanha todas as actividades e alertas da plataforma.
          </p>
        </div>

        <!-- Bulk Actions -->
        <div class="flex items-center gap-2 shrink-0">
          <UButton
            v-if="unreadCount > 0"
            size="sm"
            color="neutral"
            variant="outline"
            icon="i-lucide-check-check"
            label="Marcar todas como lidas"
            @click="markAllAsRead"
          />
          <UButton
            v-if="notifications.length > 0"
            size="sm"
            color="error"
            variant="outline"
            icon="i-lucide-trash-2"
            label="Limpar todas"
            @click="clearAll"
          />
        </div>
      </div>

      <!-- Tab Filter -->
      <div
        class="flex items-center gap-0 border-b border-gray-200 dark:border-gray-800"
      >
        <button
          class="px-4 py-2.5 text-sm font-medium border-b-2 transition-colors -mb-px"
          :class="
            activeTab === 'all'
              ? 'border-primary-500 text-primary-600 dark:text-primary-400'
              : 'border-transparent text-gray-500 dark:text-gray-400 hover:text-gray-700 dark:hover:text-gray-300'
          "
          @click="activeTab = 'all'"
        >
          Todas
          <UBadge color="neutral" variant="subtle" size="xs" class="ml-1.5">
            {{ notifications.length }}
          </UBadge>
        </button>
        <button
          class="px-4 py-2.5 text-sm font-medium border-b-2 transition-colors -mb-px"
          :class="
            activeTab === 'unread'
              ? 'border-primary-500 text-primary-600 dark:text-primary-400'
              : 'border-transparent text-gray-500 dark:text-gray-400 hover:text-gray-700 dark:hover:text-gray-300'
          "
          @click="activeTab = 'unread'"
        >
          Não lidas
          <UBadge
            v-if="unreadCount > 0"
            color="error"
            variant="subtle"
            size="xs"
            class="ml-1.5"
          >
            {{ unreadCount }}
          </UBadge>
        </button>
      </div>

      <!-- Empty State -->
      <div
        v-if="filteredNotifications.length === 0"
        class="flex flex-col items-center justify-center py-20 text-center"
      >
        <div
          class="h-16 w-16 rounded-full bg-gray-100 dark:bg-gray-800 flex items-center justify-center mb-4"
        >
          <UIcon name="i-lucide-bell-off" class="h-7 w-7 text-gray-400" />
        </div>
        <p class="text-sm font-semibold text-gray-700 dark:text-gray-200">
          Sem notificações
        </p>
        <p class="text-xs text-gray-400 dark:text-gray-500 mt-1 max-w-xs">
          {{
            activeTab === "unread"
              ? "Estás em dia! Todas as notificações foram lidas."
              : "Não tens nenhuma notificação de momento."
          }}
        </p>
        <UButton
          v-if="activeTab === 'unread'"
          size="sm"
          color="neutral"
          variant="ghost"
          label="Ver todas"
          class="mt-4"
          @click="activeTab = 'all'"
        />
      </div>

      <!-- Notifications List -->
      <div v-else class="space-y-3">
        <div v-for="notif in filteredNotifications" :key="notif.id">
          <UCard
            :class="[
              'transition-all duration-200',
              !notif.read
                ? 'ring-1 ring-primary-200 dark:ring-primary-800/60'
                : '',
            ]"
          >
            <div class="flex items-start gap-4">
              <!-- Icon Avatar -->
              <div
                class="h-10 w-10 rounded-full flex items-center justify-center shrink-0 mt-0.5"
                :class="bgByType[notif.type]"
              >
                <UIcon
                  :name="iconByType[notif.type]"
                  class="h-5 w-5"
                  :class="colorByType[notif.type]"
                />
              </div>

              <!-- Content -->
              <div class="flex-1 min-w-0">
                <!-- Title Row -->
                <div class="flex items-start justify-between gap-3">
                  <div class="flex items-center gap-2 flex-wrap">
                    <p
                      class="text-sm font-semibold text-gray-900 dark:text-white"
                    >
                      {{ notif.title }}
                    </p>
                    <UBadge
                      :color="badgeColorByType[notif.type]"
                      variant="subtle"
                      size="xs"
                    >
                      {{ labelByType[notif.type] }}
                    </UBadge>
                    <span
                      v-if="!notif.read"
                      class="h-2 w-2 rounded-full bg-primary-500 shrink-0 inline-block"
                    />
                  </div>
                  <span
                    class="text-xs text-gray-400 dark:text-gray-500 shrink-0 mt-0.5"
                  >
                    {{ notif.time }}
                  </span>
                </div>

                <!-- Body -->
                <p
                  class="text-sm text-gray-500 dark:text-gray-400 mt-1.5 leading-relaxed"
                >
                  {{ notif.body }}
                </p>

                <!-- Project tag -->
                <div
                  v-if="notif.projectTitle"
                  class="flex items-center gap-1.5 mt-2"
                >
                  <UIcon
                    name="i-lucide-folder"
                    class="h-3.5 w-3.5 text-gray-400"
                  />
                  <span class="text-xs text-gray-400 dark:text-gray-500">
                    {{ notif.projectTitle }}
                  </span>
                </div>

                <!-- Contract Invite Actions -->
                <div
                  v-if="notif.type === 'contract_invite'"
                  class="flex items-center gap-2 mt-3 pt-3 border-t border-gray-100 dark:border-gray-800"
                >
                  <UButton
                    size="xs"
                    color="primary"
                    variant="solid"
                    icon="i-lucide-check"
                    label="Aceitar convite"
                    @click="markAsRead(notif.id)"
                  />
                  <UButton
                    size="xs"
                    color="neutral"
                    variant="outline"
                    icon="i-lucide-x"
                    label="Recusar"
                  />
                </div>

                <!-- Notification Actions -->
                <div class="flex items-center gap-1 mt-3">
                  <UButton
                    v-if="!notif.read"
                    size="xs"
                    color="neutral"
                    variant="ghost"
                    icon="i-lucide-check"
                    label="Marcar como lida"
                    @click="markAsRead(notif.id)"
                  />
                  <UButton
                    size="xs"
                    color="error"
                    variant="ghost"
                    icon="i-lucide-trash-2"
                    label="Eliminar"
                    @click="removeNotification(notif.id)"
                  />
                </div>
              </div>
            </div>
          </UCard>
        </div>
      </div>
    </div>
  </AppLayoutWrapper>
</template>
