<script lang="ts" setup>
defineProps<{ title: string; value: string }>();
</script>

<template>
  <span class="inline-block space-x-2 text-sm font-medium">
    <i>{{ title }}:</i> <i class="text-slate-300">{{ value }}</i>
  </span>
</template>
