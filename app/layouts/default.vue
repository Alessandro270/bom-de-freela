<template>
  <div>
    <LayoutHeader />
    <main
      class="relative min-h-screen flex items-center justify-center px-20 py-14 text-slate-50 from-[#0b122d] to-purple-950 bg-linear-to-tl"
    >
      <slot />
    </main>
    <LayoutFooter />
  </div>
</template>
