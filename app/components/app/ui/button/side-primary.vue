<script lang="ts" setup>
defineProps<{ type?: "submit" | "button" | "reset" }>();
const styles =
  "px-4 py-2 rounded-xs flex items-center justify-between uppercase w-max text-xs font-bold bg-purple-700 hover:bg-purple-600 text-white transition-colors cursor-pointer";
</script>

<template>
  <button :class="styles" :type="type" v-if="type">
    <slot />
  </button>
  <NuxtLink v-else :class="styles">
    <slot />
  </NuxtLink>
</template>
