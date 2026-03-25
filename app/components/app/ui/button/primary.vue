<script lang="ts" setup>
const props = defineProps<{
  to?: string;
  type?: "submit" | "reset" | "button";
}>();
const styles =
  "bg-purple-700 hover:bg-transparent py-1.5 uppercase text-sm border border-slate-700 text-slate-50 active:bg-purple-900 w-full text-center inline-block rounded-md cursor-pointer font-semibold transition leading-5";
</script>

<template>
  <button :class="styles" :type="type" v-if="type">
    <slot />
  </button>
  <NuxtLink :to="to ?? '/'" :class="styles" v-else>
    <slot />
  </NuxtLink>
</template>
