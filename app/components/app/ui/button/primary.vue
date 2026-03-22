<script lang="ts" setup>
const props = defineProps<{ to?: string }>();
</script>

<template>
  <NuxtLink
    :to="to ?? '/'"
    class="hover:bg-purple-700 hover:border-transparent py-1.5 uppercase text-sm border border-slate-700 text-slate-200 active:bg-purple-900 w-full text-center inline-block rounded-md cursor-pointer font-semibold transition"
  >
    <slot />
  </NuxtLink>
</template>
