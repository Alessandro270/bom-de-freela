<script lang="ts" setup>
defineProps<{ name: string; title: string; clients: number }>();
</script>

<template>
  <li
    class="p-2.5 w-full rounded-md bg-slate-950 flex items-center space-x-4.5"
  >
    <span
      class="flex rounded-sm items-center justify-center h-10 w-10 bg-purple-700"
    >
      <Icon :name="name" class="h-4 w-4 text-3xl text-slate-200" mode="css" />
    </span>
    <div class="flex flex-col space-y-1 self-start">
      <span class="inline-block text-sm font-semibold"> {{ title }}</span>
      <span class="inline-block text-xs font-medium">
        {{ clients }} contratantes</span
      >
    </div>
  </li>
</template>
