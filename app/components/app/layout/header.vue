<template>
  <header class="bg-slate-800 px-20 h-17 flex items-center">
    <UiLogo size="md" />
    <nav class="ml-10 h-full">
      <ul class="flex items-center space-x-6 h-full">
        <li>
          <AppUiLinkNav to="/app/proposals"> Propostas </AppUiLinkNav>
        </li>
        <li>
          <AppUiLinkNav to="/app/freelancers">Freelancers</AppUiLinkNav>
        </li>
      </ul>
    </nav>

    <div
      class="ml-auto bg-slate-900 px-2 py-1.5 space-x-2 flex items-center rounded-full mr-6"
    >
      <label for="search" class="flex items-center">
        <Icon
          name="mingcute:search-line"
          class="text-xl text-slate-600 font-semibold"
        />
      </label>
      <input
        type="search"
        placeholder="pesquisar..."
        name="search"
        id="search"
        class="outline-0"
      />
    </div>
    <ul class="flex gap-4 items-center-safe justify-center">
      <li class="flex items-center">
        <Icon
          class="text-xl text-slate-50 h-full"
          name="solar:bell-line-duotone"
        />
      </li>
      <li>
        <AppUiButtonAvatar name="Alessandro Almeida" />
      </li>
    </ul>
  </header>
</template>
