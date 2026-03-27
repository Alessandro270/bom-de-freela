<script lang="ts" setup>
defineProps<{ title?: string }>();
</script>

<template>
  <div class="w-full mx-auto max-w-5xl px-6 py-7 space-y-5">
    <!-- Breadcrumb Navigation -->
    <AppUiNavBreadcrumb />

    <!-- Optional page title via prop -->
    <AppUiHeaderTitle v-if="title">{{ title }}</AppUiHeaderTitle>

    <slot />
  </div>
</template>
