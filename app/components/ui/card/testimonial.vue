<script lang="ts" setup>
defineProps<{
  name: string;
  title: string;
  rating: number;
}>();
</script>

<template>
  <li class="flex flex-col h-48 w-full rounded-md bg-slate-950 px-5 py-4">
    <UiRating :value="rating" />
    <p class="text-sm mb-3 text-justify">
      <slot />
    </p>
    <div class="flex mt-auto ml-auto space-x-3">
      <div class="flex flex-col space-y-1 text-sm">
        <span class="font-semibold capitalize">{{ name }}</span>
        <span class="text-xs capitalize">{{ title }}</span>
      </div>
      <span
        class="flex items-center justify-center h-10 w-10 rounded-full bg-purple-600 font-semibold"
      >
        {{
          name
            .split(" ")
            .map((str: string) => str[0])
            .join("")
        }}
      </span>
    </div>
  </li>
</template>
