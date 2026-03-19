<script lang="ts" setup></script>

<template>
  <header
    class="bg-slate-950 w-full text-slate-50 h-20 px-20 flex items-center"
  >
    <UiLogo />
    <nav class="ml-auto flex">
      <ul class="flex space-x-4 font-medium">
        <li><UiButtonNav to="/"> Sobre nós</UiButtonNav></li>
        <li><UiButtonNav to="/">Como funciona</UiButtonNav></li>
        <li><UiButtonNav to="/">Freelancers</UiButtonNav></li>
        <li><UiButtonNav to="/">Suporte</UiButtonNav></li>
      </ul>
    </nav>
    <ul class="flex space-x-6 items-center ml-30 font-semibold">
      <li>
        <UiButtonNav to="/auth/login">Entrar</UiButtonNav>
      </li>
      <li>
        <UiButtonCta to="/auth/sign-up"> Comece agora </UiButtonCta>
      </li>
    </ul>
  </header>
</template>
