<script lang="ts" setup>
defineProps<{
  name: string;
  sentAt: string;
  value: string;
}>();
</script>

<template>
  <div class="bg-slate-950 px-6 py-5 rounded-sm flex items-start gap-5">
    <!-- Avatar -->
    <AppUiButtonSquareAvatar :name="name" class="shrink-0" />

    <!-- Content -->
    <div class="flex-1 min-w-0 space-y-3">
      <!-- Header row: name + value -->
      <div class="flex items-start justify-between gap-4">
        <div>
          <p class="text-slate-100 font-semibold text-base leading-tight">
            {{ name }}
          </p>
          <p class="text-slate-500 text-xs mt-1">Enviado em {{ sentAt }}</p>
        </div>
        <span class="text-purple-400 font-semibold text-sm shrink-0">
          {{ value }}
        </span>
      </div>

      <p class="text-slate-300 text-sm leading-relaxed text-justify">
        <slot />
      </p>

      <div class="flex items-center gap-2 pt-1">
        <AppUiButtonSidePrimary> Aceitar </AppUiButtonSidePrimary>
        <AppUiButtonSideSecondary> Rejeitar </AppUiButtonSideSecondary>
      </div>
    </div>
  </div>
</template>
