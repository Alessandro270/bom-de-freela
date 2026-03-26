<script lang="ts" setup>
defineProps<{ title: string; description: string }>();
</script>
<template>
  <div>
    <AppUiHeaderSubtle>{{ title }}</AppUiHeaderSubtle>
    <span class="text-slate-100">{{ description }}</span>
  </div>
</template>
