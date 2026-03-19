<script lang="ts" setup></script>

<template>
  <header class="bg-slate-950 text-slate-50 h-20 px-16 flex items-center">
    <h1 class="text-lg font-semibold capitalize flex items-center space-x-2">
      <Icon
        name="line-md:briefcase-check-filled"
        class="text-purple-600"
        size="1.95rem"
        mode="svg"
      />
      <span>bom de freela</span>
    </h1>
    <nav class="ml-auto flex">
      <ul class="flex space-x-4 font-medium">
        <li><UiButtonNav to="/"> Sobre nós</UiButtonNav></li>
        <li><UiButtonNav to="/">Como funciona</UiButtonNav></li>
        <li><UiButtonNav to="/">Freelancers</UiButtonNav></li>
        <li><UiButtonNav to="/">Contato</UiButtonNav></li>
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
