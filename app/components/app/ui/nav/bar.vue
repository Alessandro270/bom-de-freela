<script lang="ts" setup>
defineProps<{ items: { to: string; label: string }[] }>();
</script>

<template>
  <nav>
    <ul
      class="grid gap-4 *:text-center font-google bg-slate-950 py-[0.39rem] rounded-sm px-1.5"
      :class="`grid-cols-${items.length}`"
    >
      <AppUiLinkProfileNav v-for="item in items" :to="item.to">
        {{ item.label }}
      </AppUiLinkProfileNav>
    </ul>
  </nav>
</template>
