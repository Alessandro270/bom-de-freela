<script lang="ts" setup>
defineProps<{ step: number; title: string }>();
</script>

<template>
  <li class="flex flex-col gap-3 rounded-md px-5 py-4 bg-slate-950">
    <div
      class="text-xl font-semibold h-14 rounded-full w-14 bg-purple-600 flex items-center justify-center"
    >
      <span class="inline-block">{{ step }}</span>
    </div>
    <div class="text-sm text-justify flex flex-col gap-2">
      <span class="font-semibold">{{ title }}</span>
      <p class="text-xs text-slate-200">
        <slot />
      </p>
    </div>
  </li>
</template>
