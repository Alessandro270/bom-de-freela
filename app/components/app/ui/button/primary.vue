<script lang="ts" setup>
const props = defineProps<{ to?: string }>();
</script>

<template>
  <NuxtLink
    :to="to ?? '/'"
    class="bg-purple-700 hover:bg-transparent py-1.5 uppercase text-sm border border-slate-700 text-slate-200 active:bg-purple-900 w-full text-center inline-block rounded-md cursor-pointer font-semibold transition leading-5"
  >
    <slot />
  </NuxtLink>
</template>
