<script lang="ts" setup>
defineProps<{ value: number }>();
</script>

<template>
  <li class="text-slate-50 flex items-center justify-between py-4">
    <AppUiButtonTag>
      <slot />
    </AppUiButtonTag>

    <UiRating :value="value" />
  </li>
</template>
