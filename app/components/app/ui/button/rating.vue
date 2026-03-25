<script setup lang="ts">
const props = defineProps<{ rating: number }>();
const rating = ref(props.rating);
const hovered = ref(0);
const stars = 5;
const active = computed(() => hovered.value || rating.value);
</script>

<template>
  <div class="flex gap-1">
    <button
      v-for="star in stars"
      :key="star"
      type="button"
      @click="rating = star"
      @mouseenter="hovered = star"
      @mouseleave="hovered = 0"
      class="focus:outline-none"
    >
      <Transition mode="out-in">
        <Icon
          :name="star <= active ? 'codicon:star-full' : 'codicon:star-empty'"
          class="text-amber-300"
          :key="star"
        />
      </Transition>
    </button>
  </div>
</template>
