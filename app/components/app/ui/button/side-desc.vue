<script lang="ts" setup>
defineProps<{
  title: string;
  value: string;
}>();
</script>

<template>
  <li
    class="text-slate-400 font-medium w-full font-google flex items-center justify-between"
  >
    <span>{{ title }}:</span> <span class="text-slate-300">{{ value }}</span>
  </li>
</template>
