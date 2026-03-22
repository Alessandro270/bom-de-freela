<script lang="ts" setup>
defineProps<{ name: string }>();
</script>

<template>
  <li class="text-slate-400 space-x-4 flex items-center">
    <span class="checkbox flex items-center">
      <input type="checkbox" :name="name" :id="name" class="h-fit" />

      <span class="inline-block box"></span>
    </span>
    <label :for="name">
      <slot />
    </label>
  </li>
</template>

<style lang="scss" scoped>
.checkbox {
  position: relative;
  & input {
    opacity: 0;
    height: 1.3rem;
    width: 1.3rem;

    position: absolute;
    inset: 0;
  }
  & .box {
    height: 1.2rem;
    width: 1.2rem;
    border-radius: 0.3rem;
    background: transparent;
    border: 2px solid var(--color-slate-600);
  }
  & input:checked ~ .box {
    background: var(--color-purple-700);
  }
}
</style>
