<script lang="ts" setup></script>

<template>
  <header
    class="bg-slate-950 w-full text-slate-50 py-4 px-20 flex items-center"
  >
    <UiLogo />
    <nav class="ml-16">
      <ul class="flex space-x-6">
        <li>
          <UiButtonNav to="/">Encontrar Propostas</UiButtonNav>
        </li>
        <li>
          <UiButtonNav to="/">Encontrar Freelancers</UiButtonNav>
        </li>
        <li></li>
      </ul>
    </nav>
    <ul class="flex space-x-6 items-center ml-auto font-semibold">
      <li>
        <UiButtonNav to="/auth/login">Entrar</UiButtonNav>
      </li>
      <li>
        <UiButtonCta to="/auth/sign-up"> Comece agora </UiButtonCta>
      </li>
    </ul>
  </header>
</template>
