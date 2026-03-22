<script lang="ts" setup>
defineProps<{ value: number }>();
</script>

<template>
  <span class="flex gap-0.5 mb-2">
    <Icon
      name="codicon:star-full"
      class="text-amber-300"
      :key="i"
      v-for="i in value"
    />
    <Icon
      name="codicon:star-empty"
      class="text-amber-300"
      :key="i"
      v-for="i in 5 - value"
    />
  </span>
</template>
