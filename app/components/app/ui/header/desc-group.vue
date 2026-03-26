<script lang="ts" setup>
defineProps<{ title: string; description: string }>();
</script>

<template>
  <div>
    <span class="capitalize text-sm block text-slate-200 font-google">
      {{ title }}
    </span>
    <span
      class="capitalize block text-slate-400 text-xs font-google font-light"
    >
      {{ description }}
    </span>
  </div>
</template>
