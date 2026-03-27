<script lang="ts" setup>
const props = defineProps<{
  role: string;
  firstName: string;
  lastName: string;
  nif: string;
  email: string;
  phone: string;
  location?: string;
}>();

const fullName = computed(() => `${props.firstName} ${props.lastName}`);
</script>

<template>
  <UCard variant="outline" class="border border-white/5">
    <template #header>
      <AppUiHeaderSubtle size="md"> Dados do {{ role }} </AppUiHeaderSubtle>
    </template>

    <div class="space-y-4">
      <div class="flex items-center space-x-3">
        <AppUiButtonAvatar :name="fullName" />
        <AppUiHeaderDescGroup :title="fullName" :description="role" />
      </div>

      <USeparator />

      <div class="grid grid-cols-2 gap-x-4 gap-y-4">
        <AppUiHeaderDescGroup
          reverse
          title="Primeiro nome"
          :description="firstName"
        />
        <AppUiHeaderDescGroup
          reverse
          title="Último nome"
          :description="lastName"
        />
        <AppUiHeaderDescGroup reverse title="NIF" :description="nif" />
        <AppUiHeaderDescGroup reverse title="Email" :description="email" />
        <AppUiHeaderDescGroup reverse title="Telefone" :description="phone" />
        <AppUiHeaderDescGroup
          v-if="location"
          reverse
          title="Localização"
          :description="location"
        />
      </div>
    </div>
  </UCard>
</template>
