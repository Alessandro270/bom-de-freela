<script lang="ts" setup>
defineProps<{ name: string }>();
</script>
<template>
  <div
    class="bg-purple-600 text-slate-50 font-semibold text-sm flex items-center justify-center h-9 w-9 rounded-full"
  >
    <span>
      {{
        name
          .split(" ")
          .map((name) => name.at(0))
          .join("")
      }}
    </span>
  </div>
</template>
