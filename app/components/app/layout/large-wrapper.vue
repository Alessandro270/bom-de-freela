<template>
  <div class="w-full max-w-7xl mx-auto space-y-5">
    <!-- Breadcrumb Navigation -->
    <AppUiNavBreadcrumb />

    <!-- Sidebar + Main content -->
    <div class="flex gap-8 items-start">
      <slot />
    </div>
  </div>
</template>
