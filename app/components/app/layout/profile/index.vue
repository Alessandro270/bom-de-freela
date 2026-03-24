<template>
  <div class="max-w-5xl mx-auto space-y-6">
    <nav>
      <ul
        class="flex gap-4 text-sm font-medium *:border-b *:border-slate-700 *:pb-1 text-slate-300"
      >
        <li>
          <NuxtLink to="/app/profile/freelancer/">
            Perfil de Freelancer
          </NuxtLink>
        </li>
        <li>
          <NuxtLink to="/app/profile/client/"> Perfil de Cliente </NuxtLink>
        </li>

        <li>
          <NuxtLink to="/app/profile/"> Usuário </NuxtLink>
        </li>
      </ul>
    </nav>
    <div>
      <slot />
    </div>
  </div>
</template>
