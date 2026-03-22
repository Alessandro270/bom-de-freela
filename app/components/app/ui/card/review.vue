<script lang="ts" setup>
defineProps<{ name: string }>();
</script>

<template>
  <li
    class="min-h-30 border-b space-y-2.5 text-justify border-slate-700 flex flex-col px-5 py-6"
  >
    <div class="flex space-x-4">
      <AppUiButtonAvatar :name="name" />
      <div>
        <span class="inline-block font-medium font-google text-">{{
          name
        }}</span>
        <UiRating :value="4" />
      </div>
    </div>
    <p class="text-sm font-medium">
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Tempore
      voluptatum dolorem qui ex? Quia natus aliquid, magni ad quidem accusantium
      molestiae architecto deserunt deleniti cumque fugiat eum ab inventore.
      Temporibus.
    </p>
  </li>
</template>
