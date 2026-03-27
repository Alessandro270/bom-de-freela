<template>
  <UCard class="hover:ring-1 hover:ring-primary-500/50 transition-all group">
    <div class="flex flex-col gap-5">
      <!-- Header: Avatar + Info + CTA -->
      <div class="flex items-start justify-between gap-6">
        <div class="flex items-center gap-5">
          <div
            class="h-16 w-16 rounded-xl bg-blue-600 flex items-center justify-center text-xl font-bold text-white select-none shrink-0"
          >
            AA
          </div>
          <div class="space-y-1">
            <div class="flex items-center gap-2">
              <h3
                class="text-lg font-bold text-gray-900 dark:text-white group-hover:text-primary-500 transition-colors"
              >
                Alessandro Almeida
              </h3>
              <UBadge color="info" variant="subtle" size="xs">Cliente</UBadge>
            </div>
            <p class="text-sm font-medium text-gray-500 dark:text-gray-400 flex items-center gap-1">
              <UIcon name="i-lucide-map-pin" class="h-3 w-3" />
              Luanda, Angola
            </p>
            <div class="flex items-center gap-1.5">
              <UiRating :value="4" />
              <span class="text-xs text-gray-400 dark:text-gray-500"
                >(18 avaliações)</span
              >
            </div>
          </div>
        </div>

        <div class="flex flex-col items-end gap-2 shrink-0">
          <div class="text-right">
            <p
              class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide"
            >
              Projetos publicados
            </p>
            <p class="text-sm font-bold text-gray-900 dark:text-white">12</p>
          </div>
          <UButton
            to="/app/clients/1"
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
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium
        voluptatem eveniet non, fugiat tempore perspiciatis nemo corrupti
        deserunt quaerat reprehenderit consequatur quidem vitae.
      </p>

      <!-- Sectors + Trust Signals -->
      <div class="flex items-center justify-between gap-4">
        <div class="flex items-center gap-2 flex-wrap">
          <span
            class="text-xs font-medium text-gray-500 dark:text-gray-400 uppercase tracking-wide shrink-0"
            >Setores:</span
          >
          <UBadge color="neutral" variant="subtle" size="sm">Tecnologia</UBadge>
          <UBadge color="neutral" variant="subtle" size="sm">Startups</UBadge>
        </div>
        <div class="flex items-center gap-1 text-xs text-success-500 shrink-0">
          <UIcon name="i-lucide-shield-check" class="h-3.5 w-3.5" />
          <span class="font-medium">Pagamento verificado</span>
        </div>
      </div>
    </div>
  </UCard>
</template>
