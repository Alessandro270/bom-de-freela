<script lang="ts" setup>
defineProps<{
  title: string;
  description: string;
}>();
</script>

<template>
  <div>
    <span class="text-sm uppercase font-bold text-purple-600"
      >{{ title }}
    </span>
    <h2 class="text-4xl font-bold">{{ description }}</h2>
  </div>
</template>
