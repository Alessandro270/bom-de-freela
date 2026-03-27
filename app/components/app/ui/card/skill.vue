<script lang="ts" setup>
defineProps<{ value: number }>();
</script>

<template>
  <li class="flex items-center justify-between py-3">
    <UBadge color="primary" variant="subtle" size="sm">
      <slot />
    </UBadge>
    <UiRating :value="value" />
  </li>
</template>
