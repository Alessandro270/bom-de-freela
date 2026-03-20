<script lang="ts" setup></script>

<template>
  <header
    class="bg-slate-950 w-full text-slate-50 h-20 px-20 flex items-center"
  >
    <UiLogo />
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

