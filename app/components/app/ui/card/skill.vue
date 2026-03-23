<template>
  <li class="text-slate-50 flex items-center justify-between py-4">
    <AppUiButtonTag>
      <slot />
    </AppUiButtonTag>

    <UiRating :value="4" />
  </li>
</template>
