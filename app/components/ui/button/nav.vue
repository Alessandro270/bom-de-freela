<script lang="ts" setup>
defineProps<{ to: string }>();
</script>
<template>
  <NuxtLink
    :to="to"
    class="inline-block font-semibold cursor-pointer hover:brightness-80 transition"
  >
    <slot />
  </NuxtLink>
</template>
