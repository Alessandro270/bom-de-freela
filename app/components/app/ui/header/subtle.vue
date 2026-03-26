<script lang="ts" setup>
const props = defineProps<{ size?: "sm" | "md" | "lg" }>();
const styles =
  props.size === "lg"
    ? "text-sm font-light"
    : props.size === "md"
      ? "text-xs font-medium"
      : "text-[0.65rem] font-medium";
</script>

<template>
  <span class="uppercase block text-slate-400 font-google" :class="styles">
    <slot />
  </span>
</template>
