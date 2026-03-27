<template>
  <UCard class="hover:ring-1 hover:ring-primary-500/50 transition-all group">
    <div class="flex flex-col gap-5">
      <!-- Header: Title + CTA -->
      <div class="flex items-start justify-between gap-6">
        <div class="space-y-2 flex-1 min-w-0">
          <NuxtLink
            to="/app/proposals/1"
            class="text-lg font-bold text-gray-900 dark:text-white group-hover:text-primary-500 transition-colors leading-snug line-clamp-2"
          >
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at
            ratione totam fugiat omnis nobis iste placeat.
          </NuxtLink>
          <div class="flex items-center gap-4 flex-wrap">
            <UiRating :value="3" />
            <span class="text-xs text-gray-400 dark:text-gray-500">
              Publicado em:
              <span class="text-gray-600 dark:text-gray-300 font-medium"
                >12/03/2026</span
              >
            </span>
            <span class="text-xs text-gray-400 dark:text-gray-500">
              Propostas:
              <span class="text-gray-600 dark:text-gray-300 font-medium"
                >10</span
              >
            </span>
          </div>
        </div>

        <div class="flex flex-col items-end gap-2 shrink-0">
          <p class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide">
            Preço inicial
          </p>
          <p class="text-base font-bold text-primary-500">500 mil Kz</p>
          <UButton
            to="/app/proposals/1"
            size="xs"
            color="primary"
            variant="solid"
            label="Fazer proposta"
            icon="i-lucide-send"
          />
        </div>
      </div>

      <!-- Description -->
      <p
        class="text-sm text-gray-600 dark:text-gray-400 leading-relaxed line-clamp-2 text-justify"
      >
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum sapiente
        quia numquam hic. Consequatur vitae sit harum impedit esse, sapiente
        aspernatur expedita. Obcaecati, voluptatem deleniti.
      </p>

      <!-- Footer: Client + Tags -->
      <div class="flex items-center justify-between gap-4 pt-1">
        <div class="flex items-center gap-3">
          <UAvatar alt="Alessandro Almeida" size="xs" class="bg-blue-600 shrink-0" />
          <div>
            <p class="text-xs font-semibold text-gray-700 dark:text-gray-300">
              Alessandro Almeida
            </p>
            <p class="text-xs text-gray-400 dark:text-gray-500">
              Última proposta: há 7 horas
            </p>
          </div>
        </div>
        <div class="flex items-center gap-1.5 flex-wrap">
          <UBadge color="neutral" variant="subtle" size="xs">Python</UBadge>
          <UBadge color="neutral" variant="subtle" size="xs">Backend</UBadge>
          <UBadge color="neutral" variant="subtle" size="xs">PWA</UBadge>
        </div>
      </div>
    </div>
  </UCard>
</template>
