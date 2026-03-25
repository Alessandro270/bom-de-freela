<script lang="ts" setup>
defineProps<{ title: string }>();
</script>

<template>
  <div class="max-w-5xl space-y-4 mx-auto bg-slate-950 px-6 py-7">
    <AppUiHeaderTitle>{{ title }}</AppUiHeaderTitle>
    <slot />
  </div>
</template>
