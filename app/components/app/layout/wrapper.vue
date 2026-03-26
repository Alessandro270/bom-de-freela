<script lang="ts" setup>
defineProps<{ title?: string }>();
</script>

<template>
  <div class="w-full space-y-4 mx-auto max-w-5xl px-6 py-7">
    <AppUiHeaderTitle v-if="title">{{ title }}</AppUiHeaderTitle>
    <slot />
  </div>
</template>
