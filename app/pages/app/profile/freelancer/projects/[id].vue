<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutWrapper>
    <div class="space-y-6">
      <UCard variant="subtle">
        <template #header>
          <div class="space-y-2">
            <h1>Desenvolvimento de uma plataforma de freelancing digital</h1>
            <div class="space-x-2">
              <UBadge color="neutral" variant="outline">Categoria</UBadge>
              <UBadge color="neutral" variant="outline">Subcategoria</UBadge>
              <UBadge color="neutral" variant="outline">Prazo: 30 dias</UBadge>
            </div>
          </div>
        </template>
      </UCard>
      <div class="flex space-x-30">
        <AppUiHeaderGroup
          title="Valor do contrato"
          description="AOA 250.000 "
        />
        <AppUiHeaderGroup title="Prazo de entrega" description="30 dias " />
        <AppUiHeaderGroup title="Aceite em " description="15/03/2026" />
      </div>
      <div class="flex space-x-4">
        <UCard variant="subtle">
          <AppUiHeaderSubtle size="md">Dados do cliente</AppUiHeaderSubtle>
          <div class="flex py-3 space-x-4">
            <AppUiButtonAvatar name="António Costa" />
            <AppUiHeaderDescGroup title="António Costa" description="cliente" />
          </div>
          <USeparator />
          Primeiro nome António Último nome Costa NIF do cliente 5 417 835 LA
          042 Email a.costa@empresa.ao Telefone +244 923 456 789
        </UCard>
        <UCard variant="subtle">
          <AppUiHeaderSubtle size="md">Dados do freelancer</AppUiHeaderSubtle>
          <div class="flex space-x-4">
            <AppUiButtonAvatar name="Manuel Silva" />
            <AppUiHeaderDescGroup
              title="António Costa"
              description="Freelancer"
            />
          </div>
          Primeiro nome Manuel Último nome Silva NIF do freelancer 6 832 017 LB
          118 Email m.silva@freelancer.ao Telefone +244 912 345 678
        </UCard>
      </div>
    </div>
  </AppLayoutWrapper>
</template>
