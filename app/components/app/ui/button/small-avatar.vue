<script lang="ts" setup>
defineProps<{ name: string }>();
</script>

<template>
  <div
    class="h-10 w-10 rounded-xs font-semibold flex items-center justify-center bg-purple-700"
  >
    <span
      >{{
        name
          .split(" ")
          .map((s) => s[0])
          .join("")
      }}
    </span>
  </div>
</template>
