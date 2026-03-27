<script lang="ts" setup>
defineProps<{ items: { to: string; label: string }[] }>();
</script>

<template>
  <nav>
    <ul class="flex gap-1">
      <li v-for="item in items" :key="item.label">
        <NuxtLink
          :to="item.to"
          class="inline-flex items-center px-3 py-1.5 text-sm font-medium rounded-md text-gray-500 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white hover:bg-gray-100 dark:hover:bg-gray-800 transition-colors"
          active-class="text-gray-900 dark:text-white bg-gray-100 dark:bg-gray-800"
        >
          {{ item.label }}
        </NuxtLink>
      </li>
    </ul>
  </nav>
</template>
