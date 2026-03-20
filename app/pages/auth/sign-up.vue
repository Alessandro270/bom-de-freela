<template>
  <LayoutAuth>
    <template #img>
      <img
        srcset="~/assets/img/signup-desktop.jpg"
        alt="abstract-image"
        class="h-full w-full object-cover"
      />
    </template>
    <template #form>
      <div class="mb-8 text-center">
        <h1 class="text-2xl font-semibold mb-2">Cadastre-se</h1>
        <p>A tua oportunidade é agora</p>
      </div>

      <div class="w-full flex flex-col gap-4 mb-4">
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
          type="password"
        />
        <UiInputGroup
          name="confirmPassword"
          placeholder="Confirmar a senha"
          title="Confirmar palavra passe"
          type="password"
          class="mb-4"
        />
        <UiButtonCta class="w-full text-center block">Criar conta</UiButtonCta>
      </div>
      <p>
        Já possui uma conta?
        <UiLinkInline to="/auth/login">Iniciar sessão</UiLinkInline>
      </p>
    </template>
  </LayoutAuth>
</template>
