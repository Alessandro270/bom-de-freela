<script lang="ts" setup>
defineProps<{ title: string }>();
</script>

<template>
  <div class="w-full space-y-4 mx-auto px-6 py-7">
    <AppUiHeaderTitle>{{ title }}</AppUiHeaderTitle>
    <slot />
  </div>
</template>
