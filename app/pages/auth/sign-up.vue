<template>
  <div class="bg-slate-950 w-2/3 h-190 rounded-2xl flex">
    <div class="w-1/2 bg-slate-400 rounded-2xl overflow-hidden">
      <img
        src="~/assets/img/signup-mobile.jpg"
        srcset="~/assets/img/signup-desktop.jpg 2x"
        alt="abstract-image"
        class="h-full w-full object-cover"
      />
    </div>
    <form class="h-full flex flex-col w-1/2 items-center justify-center px-10">
      <div class="mb-10 text-center">
        <h1 class="text-2xl font-semibold mb-2">Cadastre-se</h1>
        <p>A tua oportunidade é agora</p>
      </div>

      <div class="w-full flex flex-col gap-4">
        <div class="flex gap-3 w-full">
          <UiInputGroup
            name="firstname"
            placeholder="Seu nome"
            title="Primeiro nome"
          />
          <UiInputGroup
            name="lastname"
            placeholder="Seu último nome"
            title="Último nome"
          />
        </div>
        <UiInputGroup
          name="email"
          placeholder="exemplo@exemplo.com"
          title="Email"
        />
        <UiInputGroup
          name="password"
          placeholder="Sua senha"
          title="Palavra passe"
        />
        <UiInputGroup
          name="confirmPassword"
          placeholder="Confirmar a senha"
          title="Confirmar palavra passe"
          class="mb-4"
        />
        <UiButtonCta class="w-full text-center block">Criar conta</UiButtonCta>
      </div>
    </form>
  </div>
</template>
