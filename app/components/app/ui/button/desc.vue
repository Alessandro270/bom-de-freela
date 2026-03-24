<script lang="ts" setup>
defineProps<{ title: string; value: string }>();
</script>

<template>
  <span class="flex space-x-2 text-sm text-slate-400 font-medium">
    <i>{{ title }}:</i> <i class="text-slate-200">{{ value }}</i>
  </span>
</template>
