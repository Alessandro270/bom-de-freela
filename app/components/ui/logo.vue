<script lang="ts" setup>
defineProps<{ to?: string; size?: string }>();
</script>

<template>
  <NuxtLink
    :to="to ?? '/'"
    class="font-semibold capitalize flex items-center space-x-2"
    :class="`text-${size || 'xl'}`"
  >
    <Icon
      name="line-md:briefcase-check-filled"
      class="text-purple-600"
      size="1.95rem"
      mode="svg"
    />
    <span class="inline-block">bom de freela</span>
  </NuxtLink>
</template>
