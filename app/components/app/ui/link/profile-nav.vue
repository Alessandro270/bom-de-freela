<script lang="ts" setup>
defineProps<{ to: string }>();
</script>

<template>
  <li class="w-full">
    <NuxtLink
      :to="to"
      class="inline-block w-full px-4 py-0.5 rounded-4xl font-medium"
    >
      <slot />
    </NuxtLink>
  </li>
</template>

<style lang="scss" scoped>
.router-link-active {
  background: var(--color-purple-700);
}
</style>
