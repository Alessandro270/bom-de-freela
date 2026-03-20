<template>
  <footer class="bg-slate-950 text-slate-50 border-t border-slate-800">
    <div class="flex flex-col md:flex-row py-12 px-20 gap-16">
      <div class="max-w-xs">
        <UiLogo class="mb-2" />
        <p class="text-slate-500 text-sm">
          A plataforma que conecta freelancers e clientes em Angola.
        </p>
      </div>
      <div>
        <h2 class="text-sm font-semibold mb-3">Plataforma</h2>
        <ul class="text-slate-500 space-y-1.5 text-sm">
          <li>Publicar Projeto</li>
          <li>Encontrar Freelancers</li>
          <li>Categorias</li>
        </ul>
      </div>
      <div>
        <h2 class="text-sm font-semibold mb-3">Conta</h2>
        <ul class="text-slate-500 space-y-1.5 text-sm">
          <li><NuxtLink to="/auth/sign-up">Criar conta</NuxtLink></li>
          <li><NuxtLink to="/auth/login">Iniciar sessão</NuxtLink></li>
        </ul>
      </div>
    </div>
    <div class="flex items-center justify-center h-14 border-t border-slate-800 text-slate-500 text-xs">
      Copyright &copy; 2026 Bom de Freela. Todos os direitos reservados.
    </div>
  </footer>
</template>

