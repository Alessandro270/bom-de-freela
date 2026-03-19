<script lang="ts" setup>
defineProps<{
  name: string;
  title: string;
  placeholder?: string;
  type?: string;
}>();
</script>

<template>
  <div class="flex flex-col gap-2 w-full">
    <label class="font-semibold text-md" :for="name">{{ title }}</label>
    <input
      class="bg-slate-900 w-full font-medium px-3 py-2 rounded-md"
      :type="type ?? 'text'"
      :name="name"
      :id="name"
      :placeholder="placeholder"
    />
  </div>
</template>
