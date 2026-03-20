<script lang="ts" setup>
defineProps<{ to?: string }>();
</script>

<template>
  <NuxtLink
    :to="to"
    class="px-4 py-2 border-2 rounded-md cursor-pointer inline-block font-semibold hover:border-slate-50 bg-purple-600 hover:bg-transparent border-purple-600 transition"
  >
    <slot />
  </NuxtLink>
</template>
