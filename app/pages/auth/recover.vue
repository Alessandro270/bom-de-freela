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
        <h1 class="text-2xl font-semibold mb-2">Recuperar senha</h1>
        <p>
          Insira o email associado à sua conta e enviaremos um link para
          redefinir a sua senha.
        </p>
      </div>
      <div class="w-full flex flex-col gap-4 mb-4">
        <UiInputGroup
          name="email"
          placeholder="exemplo@exemplo.com"
          title="Email"
          class="mb-4"
        />
        <UiButtonCta class="w-full text-center block"
          >Enviar link de recuperação</UiButtonCta
        >
      </div>

      <p>
        Lembrou da senha?
        <UiLinkInline to="/auth/login">Iniciar sessão</UiLinkInline>
      </p>
    </template>
  </LayoutAuth>
</template>
