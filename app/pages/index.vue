<template>
  <div class="min-h-screen pb-20">
    <!-- Hero Section -->
    <section class="flex flex-col items-center justify-center text-center px-6 py-32">
      <h1 class="text-4xl md:text-5xl font-semibold mb-4">
        A plataforma de prestação <br />
        <span class="inline-block bg-linear-to-tr from-purple-700 to-orange-600 bg-clip-text text-transparent">
          de serviços digitais
        </span>
        em Angola
      </h1>
      <p class="text-slate-400 text-lg max-w-xl mb-10">
        Conectamos freelancers aos melhores projetos. Publique, descubra e contrate talento especializado.
      </p>
      <div class="flex space-x-4">
        <UiButtonCta to="/auth/sign-up">
          Comece agora
        </UiButtonCta>
        <UiButtonNav to="/auth/login" class="border border-slate-700 px-4 py-2 rounded-md hover:bg-slate-800 transition">
          Entrar
        </UiButtonNav>
      </div>
    </section>

    <div class="mx-auto px-6 md:px-20 max-w-5xl space-y-28">

      <!-- O que oferecemos -->
      <section>
        <div class="text-center mb-10">
          <h2 class="text-2xl font-semibold mb-2">O que oferecemos</h2>
          <div class="w-12 h-0.5 bg-purple-600 mx-auto rounded-full"></div>
        </div>
        <div class="grid md:grid-cols-2 gap-6">
          <div class="bg-slate-950 border border-slate-800 rounded-2xl p-8 text-center">
            <Icon name="line-md:clipboard-list-twotone" class="text-3xl text-purple-500 mb-4" />
            <h3 class="text-lg font-semibold mb-2">Para Clientes</h3>
            <p class="text-slate-400 text-sm leading-relaxed">
              Publique o seu projeto e encontre profissionais experientes. Avalie propostas e comunique diretamente.
            </p>
          </div>
          <div class="bg-slate-950 border border-slate-800 rounded-2xl p-8 text-center">
            <Icon name="line-md:laptop-twotone" class="text-3xl text-orange-500 mb-4" />
            <h3 class="text-lg font-semibold mb-2">Para Freelancers</h3>
            <p class="text-slate-400 text-sm leading-relaxed">
              Crie o seu perfil, descubra projetos compatíveis com as suas habilidades e envie propostas.
            </p>
          </div>
        </div>
      </section>

      <!-- Categorias -->
      <section>
        <div class="text-center mb-10">
          <h2 class="text-2xl font-semibold mb-2">Categorias</h2>
          <div class="w-12 h-0.5 bg-purple-600 mx-auto rounded-full"></div>
        </div>
        <div class="grid grid-cols-2 lg:grid-cols-4 gap-4">
          <div class="bg-slate-950 border border-slate-800 rounded-xl p-5 text-center hover:border-purple-800 transition-colors">
            <Icon name="line-md:computer" class="text-2xl text-slate-300 mb-2" />
            <h4 class="text-sm font-medium">Programação e TI</h4>
          </div>
          <div class="bg-slate-950 border border-slate-800 rounded-xl p-5 text-center hover:border-purple-800 transition-colors">
            <Icon name="line-md:pencil" class="text-2xl text-slate-300 mb-2" />
            <h4 class="text-sm font-medium">Design e Multimédia</h4>
          </div>
          <div class="bg-slate-950 border border-slate-800 rounded-xl p-5 text-center hover:border-purple-800 transition-colors">
            <Icon name="line-md:document-list" class="text-2xl text-slate-300 mb-2" />
            <h4 class="text-sm font-medium">Redação e Tradução</h4>
          </div>
          <div class="bg-slate-950 border border-slate-800 rounded-xl p-5 text-center hover:border-purple-800 transition-colors">
            <Icon name="line-md:phone-call-twotone-loop" class="text-2xl text-slate-300 mb-2" />
            <h4 class="text-sm font-medium">Marketing Digital</h4>
          </div>
        </div>
      </section>

      <!-- Como Funciona -->
      <section>
        <div class="text-center mb-10">
          <h2 class="text-2xl font-semibold mb-2">Como Funciona</h2>
          <div class="w-12 h-0.5 bg-purple-600 mx-auto rounded-full"></div>
        </div>
        <div class="grid md:grid-cols-3 gap-6 text-center">
          <div class="flex flex-col items-center">
            <div class="w-12 h-12 bg-slate-950 border border-purple-800 rounded-full flex items-center justify-center text-lg font-bold mb-4">1</div>
            <h4 class="font-semibold mb-1">Publicar ou Encontrar</h4>
            <p class="text-slate-400 text-sm">Clientes publicam projetos e freelancers encontram oportunidades.</p>
          </div>
          <div class="flex flex-col items-center">
            <div class="w-12 h-12 bg-slate-950 border border-purple-800 rounded-full flex items-center justify-center text-lg font-bold mb-4">2</div>
            <h4 class="font-semibold mb-1">Conectar e Acordar</h4>
            <p class="text-slate-400 text-sm">Comunicação direta, envio de propostas e acordo de prazos e valores.</p>
          </div>
          <div class="flex flex-col items-center">
            <div class="w-12 h-12 bg-slate-950 border border-purple-800 rounded-full flex items-center justify-center text-lg font-bold mb-4">3</div>
            <h4 class="font-semibold mb-1">Realizar e Entregar</h4>
            <p class="text-slate-400 text-sm">O freelancer executa o trabalho e faz a entrega diretamente pela plataforma.</p>
          </div>
        </div>
      </section>

    </div>
  </div>
</template>

<script setup lang="ts">
useHead({
  title: 'Bom de Freela | A plataforma de freelancing de Angola',
})
</script>

