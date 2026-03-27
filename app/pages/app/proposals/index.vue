<script lang="ts" setup>
definePageMeta({ layout: "app" });

const search = ref("");
const selectedCategory = ref("Desenvolvimento");

const categories = [
  { label: "Desenvolvimento", count: 87 },
  { label: "Design & Criatividade", count: 64 },
  { label: "Marketing Digital", count: 43 },
  { label: "Redação & Tradução", count: 29 },
  { label: "Suporte Administrativo", count: 21 },
  { label: "Consultoria", count: 15 },
  { label: "Multimédia", count: 11 },
];
</script>

<template>
  <AppLayoutLargeWrapper>
    <!-- Sidebar Filters -->
    <aside class="w-72 shrink-0">
      <UCard class="sticky top-6">
        <template #header>
          <div class="flex items-center justify-between">
            <h2
              class="text-sm font-semibold text-gray-900 dark:text-white uppercase tracking-wide"
            >
              Filtros
            </h2>
            <UButton color="neutral" variant="ghost" size="xs" label="Limpar" />
          </div>
        </template>

        <div class="space-y-5">
          <!-- Categories -->
          <div>
            <h3
              class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wide mb-3"
            >
              Categorias
            </h3>
            <div class="space-y-0.5">
              <button
                v-for="cat in categories"
                :key="cat.label"
                class="w-full flex items-center justify-between px-2 py-1.5 rounded-md text-sm transition-colors"
                :class="
                  selectedCategory === cat.label
                    ? 'bg-primary-50 dark:bg-primary-950 text-primary-600 dark:text-primary-400 font-medium'
                    : 'text-gray-600 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-800'
                "
                @click="selectedCategory = cat.label"
              >
                <span class="truncate">{{ cat.label }}</span>
                <UBadge
                  :color="selectedCategory === cat.label ? 'primary' : 'neutral'"
                  variant="subtle"
                  size="xs"
                >
                  {{ cat.count }}
                </UBadge>
              </button>
            </div>
          </div>

          <USeparator />

          <!-- Budget Range -->
          <div>
            <h3
              class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wide mb-3"
            >
              Orçamento
            </h3>
            <div class="space-y-2 text-sm">
              <label class="flex items-center gap-2 text-gray-600 dark:text-gray-400 cursor-pointer">
                <input type="radio" name="budget" class="accent-primary-500" />
                Menos de 100 mil Kz
              </label>
              <label class="flex items-center gap-2 text-gray-600 dark:text-gray-400 cursor-pointer">
                <input type="radio" name="budget" class="accent-primary-500" checked />
                100 mil – 500 mil Kz
              </label>
              <label class="flex items-center gap-2 text-gray-600 dark:text-gray-400 cursor-pointer">
                <input type="radio" name="budget" class="accent-primary-500" />
                Mais de 500 mil Kz
              </label>
            </div>
          </div>

          <USeparator />

          <!-- Deadline -->
          <div>
            <h3
              class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wide mb-3"
            >
              Prazo
            </h3>
            <div class="space-y-2 text-sm">
              <label class="flex items-center gap-2 text-gray-600 dark:text-gray-400 cursor-pointer">
                <input type="checkbox" class="accent-primary-500" />
                Menos de 7 dias
              </label>
              <label class="flex items-center gap-2 text-gray-600 dark:text-gray-400 cursor-pointer">
                <input type="checkbox" class="accent-primary-500" />
                7 a 30 dias
              </label>
              <label class="flex items-center gap-2 text-gray-600 dark:text-gray-400 cursor-pointer">
                <input type="checkbox" class="accent-primary-500" />
                Mais de 30 dias
              </label>
            </div>
          </div>
        </div>
      </UCard>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 min-w-0 space-y-6">
      <!-- Search Bar -->
      <UInput
        v-model="search"
        icon="i-lucide-search"
        placeholder="Pesquisar projetos por título, habilidade ou categoria..."
        size="lg"
        class="w-full"
      />

      <!-- Results Header -->
      <div class="flex items-center justify-between">
        <div>
          <h1 class="text-lg font-bold text-gray-900 dark:text-white">
            Projetos em
            <span class="text-primary-500">{{ selectedCategory }}</span>
          </h1>
          <p class="text-sm text-gray-500 dark:text-gray-400 mt-0.5">
            87 projetos disponíveis
          </p>
        </div>
        <div class="flex items-center gap-2">
          <span class="text-sm text-gray-500 dark:text-gray-400">Ordem:</span>
          <USelect
            :options="['Mais recente', 'Maior orçamento', 'Menor orçamento', 'Prazo']"
            size="sm"
            class="w-44"
          />
        </div>
      </div>

      <!-- Cards List -->
      <div class="space-y-4">
        <AppUiCardProposal v-for="i in 4" :key="i" />
      </div>
    </main>
  </AppLayoutLargeWrapper>
</template>
