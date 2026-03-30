<template>
  <header
    class="sticky top-0 z-50 flex h-16 items-center gap-4 border-b border-slate-800 bg-slate-950 px-6"
  >
    <!-- Logo -->
    <NuxtLink
      to="/admin"
      class="flex items-center gap-2.5 font-semibold text-white"
    >
      <Icon
        name="line-md:briefcase-check-filled"
        class="text-primary"
        size="1.6rem"
        mode="svg"
      />
      <span class="text-sm leading-tight">
        bom de freela<br />
        <span class="text-xs font-normal text-slate-400">Admin Panel</span>
      </span>
    </NuxtLink>

    <!-- Spacer -->
    <div class="flex-1" />

    <!-- Right side actions -->
    <div class="flex items-center gap-3">
      <!-- Notifications -->
      <UButton
        icon="i-lucide-bell"
        class="relative"
        color="neutral"
        variant="ghost"
        size="sm"
      >
        <template #trailing>
          <UBadge
            size="xs"
            color="error"
            class="absolute -top-1 -right-1 rounded-full px-1 min-w-4 h-4 flex items-center justify-center text-[10px]"
          >
            5
          </UBadge>
        </template>
      </UButton>

      <!-- Admin Avatar Menu -->
      <UDropdownMenu
        :items="[[{ label: 'Sair', icon: 'i-lucide-log-out', color: 'error' }]]"
      >
        <div
          class="flex items-center gap-2.5 cursor-pointer rounded-full border border-slate-700 px-1 py-1.5 hover:border-slate-500 transition-colors"
        >
          <div
            class="h-7 w-7 rounded-full bg-primary flex items-center justify-center text-xs font-bold text-white"
          >
            A
          </div>
          <span class="text-sm text-slate-300 hidden sm:block">Admin</span>
          <Icon name="i-lucide-chevron-down" class="text-slate-500 text-xs" />
        </div>
      </UDropdownMenu>
    </div>
  </header>
</template>
