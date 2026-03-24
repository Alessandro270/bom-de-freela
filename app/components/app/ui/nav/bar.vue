<script lang="ts" setup>
defineProps<{ items: { to: string; label: string }[] }>();
</script>

<template>
  <nav>
    <ul
      class="flex gap-4 grid-cols *:text-center font-google bg-slate-950 py-[0.39rem] rounded-sm px-1.5"
    >
      <AppUiLinkProfileNav
        v-for="item in items"
        :key="item.label"
        :to="item.to"
      >
        {{ item.label }}
      </AppUiLinkProfileNav>
    </ul>
  </nav>
</template>
