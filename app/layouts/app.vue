<template>
  <div class="bg-slate-900 min-h-screen text-slate-50">
    <AppLayoutHeader />
    <main class="min-h-screen px-20 py-8">
      <slot />
    </main>
    <LayoutFooter />
  </div>
</template>
