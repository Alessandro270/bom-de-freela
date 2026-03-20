<script lang="ts" setup>
defineProps<{ to: string }>();
</script>

<template>
  <NuxtLink :to="to" class="text-purple-600 font-semibold">
    <slot />
  </NuxtLink>
</template>
