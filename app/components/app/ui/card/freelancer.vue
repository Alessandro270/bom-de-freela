<template>
  <UCard class="hover:ring-1 hover:ring-primary-500/50 transition-all group">
    <div class="flex flex-col gap-5">
      <!-- Header: Avatar + Info + CTA -->
      <div class="flex items-start justify-between gap-6">
        <div class="flex items-center gap-5">
          <div
            class="h-16 w-16 rounded-xl bg-violet-600 flex items-center justify-center text-xl font-bold text-white select-none shrink-0"
          >
            AA
          </div>
          <div class="space-y-1">
            <h3
              class="text-lg font-bold text-gray-900 dark:text-white group-hover:text-primary-500 transition-colors"
            >
              Alessandro Almeida
            </h3>
            <p class="text-sm font-medium text-gray-500 dark:text-gray-400">
              Desenvolvedor backend
            </p>
            <div class="flex items-center gap-1.5">
              <UiRating :value="4" />
              <span class="text-xs text-gray-400 dark:text-gray-500"
                >(12 projetos)</span
              >
            </div>
          </div>
        </div>

        <div class="flex flex-col items-end gap-2 shrink-0">
          <div class="text-right">
            <p
              class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
            >
              Por projeto
            </p>
            <p class="text-sm font-bold text-primary-500">500 mil Kz</p>
          </div>
          <UButton
            to="/app/freelancers/1"
            size="xs"
            color="primary"
            variant="solid"
            label="Ver perfil"
            icon="i-lucide-arrow-up-right"
            trailing
          />
        </div>
      </div>

      <!-- About -->
      <p
        class="text-sm text-gray-600 dark:text-gray-400 leading-relaxed line-clamp-2 text-justify"
      >
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Illum sapiente
        quia numquam hic. Consequatur vitae sit harum impedit esse, sapiente
        aspernatur expedita. Obcaecati, voluptatem deleniti.
      </p>

      <!-- Skills -->
      <div class="flex items-center gap-2 flex-wrap">
        <span
          class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide shrink-0"
          >Habilidades:</span
        >
        <UBadge color="primary" variant="subtle" size="sm">Python</UBadge>
        <UBadge color="primary" variant="subtle" size="sm">Backend</UBadge>
        <UBadge color="primary" variant="subtle" size="sm">PWA</UBadge>
      </div>
    </div>
  </UCard>
</template>
