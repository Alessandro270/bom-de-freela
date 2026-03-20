<template>
  <LayoutAuth>
    <template #img>
      <img
        src="
          ~/assets/img/login-desktop.svg
        "
        alt="abstract-image"
        class="h-full w-full object-cover"
      />
    </template>
    <template #form>
      <div class="mb-8 text-center">
        <h1 class="text-2xl font-semibold mb-2">Iniciar sessão</h1>
        <p>Embarque em novos projetos com o <strong>Bom De Freela</strong></p>
      </div>
      <div class="w-full flex flex-col gap-4 mb-4">
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
          class="mb-4"
        />
        <UiButtonCta class="w-full text-center block"
          >Iniciar sessão</UiButtonCta
        >
      </div>

      <p>
        Ainda não possui uma conta?
        <UiLinkInline to="/auth/sign-up">Comece agora</UiLinkInline>
      </p>
    </template>
  </LayoutAuth>
</template>
