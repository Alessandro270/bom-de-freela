<script lang="ts" setup>
defineProps<{ name: string }>();
</script>

<template>
  <div
    class="py-8 min-w-24 rounded-md flex items-center justify-center font-bold text-4xl capitalize text-slate-50 bg-purple-700"
  >
    <span class="inline-block leading-5">
      {{
        name
          .split(" ")
          .map((str) => str[0])
          .join("")
      }}
    </span>
  </div>
</template>
