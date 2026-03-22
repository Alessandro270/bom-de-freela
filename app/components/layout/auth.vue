<template>
  <div class="h-screen flex items-center justify-center">
    <div class="bg-slate-950 w-3/4 h-11/12 rounded-2xl flex">
      <div class="w-1/2 bg-slate-950 relative rounded-2xl overflow-hidden">
        <slot name="img" />
      </div>

      <form
        class="h-full flex flex-col w-1/2 items-center justify-center px-10"
      >
        <slot name="form" />
      </form>
    </div>
  </div>
</template>
