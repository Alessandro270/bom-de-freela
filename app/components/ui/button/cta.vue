<script lang="ts" setup>
const props = defineProps<{ to?: string; type?: "cta" | "rev" }>();
const btnType = !props.type ? "cta" : props.type;
const colors =
  btnType === "cta"
    ? "hover:border-slate-50 bg-purple-600 hover:bg-transparent border-purple-600"
    : "hover:border-transparent bg-transparent hover:bg-slate-950 border-transparent";
</script>

<template>
  <NuxtLink
    :to="to ?? '/'"
    class="px-4 py-2 border-2 rounded-md cursor-pointer font-semibold transition"
    :class="colors"
  >
    <slot />
  </NuxtLink>
</template>
