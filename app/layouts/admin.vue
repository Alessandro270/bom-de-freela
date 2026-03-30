<template>
  <UApp>
    <div class="min-h-screen bg-slate-800 text-slate-50 flex flex-col">
      <!-- Top Header -->
      <AdminLayoutHeader />

      <!-- Body: Sidebar + Content -->
      <div class="flex flex-1">
        <!-- Sidebar -->
        <aside
          class="w-60 shrink-0 border-r border-slate-800 bg-slate-950 px-3 py-5 sticky top-16 h-[calc(100vh-4rem)] overflow-y-auto"
        >
          <AdminLayoutSidebar />
        </aside>

        <!-- Main Content -->
        <main class="flex-1 min-w-0 p-6">
          <slot />
        </main>
      </div>
    </div>
  </UApp>
</template>
