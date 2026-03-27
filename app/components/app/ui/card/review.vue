<script lang="ts" setup>
defineProps<{ name: string }>();
</script>

<template>
  <li class="py-4 space-y-3">
    <div class="flex items-center gap-3">
      <UAvatar :alt="name" size="sm" class="bg-violet-600 shrink-0" />
      <div>
        <p class="text-sm font-semibold text-gray-900 dark:text-white">{{ name }}</p>
        <UiRating :value="4" />
      </div>
    </div>
    <p class="text-sm text-gray-600 dark:text-gray-400 leading-relaxed text-justify">
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Tempore
      voluptatum dolorem qui ex? Quia natus aliquid, magni ad quidem accusantium
      molestiae architecto deserunt deleniti cumque fugiat eum ab inventore.
    </p>
  </li>
</template>
