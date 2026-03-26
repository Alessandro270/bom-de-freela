<script lang="ts" setup>
defineProps<{ title: string; description: string; reverse?: boolean }>();
</script>

<template>
  <div>
    <span
      class="capitalize block font-google"
      :class="reverse ? 'text-slate-400 text-xs' : 'text-slate-200 text-sm '"
    >
      {{ title }}
    </span>
    <span
      class="capitalize block font-google font-light"
      :class="reverse ? 'text-slate-100 text-sm' : 'text-slate-400  text-xs'"
    >
      {{ description }}
    </span>
  </div>
</template>
