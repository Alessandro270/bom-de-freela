<script lang="ts" setup>
definePageMeta({ layout: "app" });

const search = ref("");
const selectedCategory = ref("Desenvolvimento");

const categories = [
  { label: "Desenvolvimento", count: 124 },
  { label: "Design & Criatividade", count: 86 },
  { label: "Marketing Digital", count: 52 },
  { label: "Redação & Tradução", count: 31 },
  { label: "Suporte Administrativo", count: 18 },
  { label: "Consultoria", count: 12 },
  { label: "Multimédia", count: 9 },
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
                  :color="
                    selectedCategory === cat.label ? 'primary' : 'neutral'
                  "
                  variant="subtle"
                  size="xs"
                >
                  {{ cat.count }}
                </UBadge>
              </button>
            </div>
          </div>

          <USeparator />

          <!-- Availability -->
          <div>
            <h3
              class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wide mb-3"
            >
              Disponibilidade
            </h3>
            <div class="space-y-2 text-sm">
              <label
                class="flex items-center gap-2 text-gray-600 dark:text-gray-400 cursor-pointer"
              >
                <input type="checkbox" class="accent-primary-500" />
                Tempo Inteiro
              </label>
              <label
                class="flex items-center gap-2 text-gray-600 dark:text-gray-400 cursor-pointer"
              >
                <input type="checkbox" class="accent-primary-500" />
                Meio Tempo
              </label>
              <label
                class="flex items-center gap-2 text-gray-600 dark:text-gray-400 cursor-pointer"
              >
                <input type="checkbox" class="accent-primary-500" />
                Fim de Semana
              </label>
            </div>
          </div>

          <USeparator />

          <!-- Rating -->
          <div>
            <h3
              class="text-xs font-semibold text-gray-500 dark:text-gray-400 uppercase tracking-wide mb-3"
            >
              Avaliação Mínima
            </h3>
            <div class="space-y-2 text-sm">
              <label
                v-for="stars in [5, 4, 3]"
                :key="stars"
                class="flex items-center gap-2 text-gray-600 dark:text-gray-400 cursor-pointer"
              >
                <input type="radio" name="rating" class="accent-primary-500" />
                <UiRating :value="stars" />
                <span class="text-xs">e acima</span>
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
        placeholder="Pesquisar freelancers por nome, habilidade ou cargo..."
        size="lg"
        class="w-full"
      />

      <!-- Results Header -->
      <div class="flex items-center justify-between">
        <div>
          <h1 class="text-lg font-bold text-gray-900 dark:text-white">
            Freelancers em
            <span class="text-primary-500">{{ selectedCategory }}</span>
          </h1>
          <p class="text-sm text-gray-500 dark:text-gray-400 mt-0.5">
            124 profissionais encontrados
          </p>
        </div>
        <div class="flex items-center gap-2">
          <span class="text-sm text-gray-500 dark:text-gray-400">Ordem:</span>
          <USelect
            :options="['Relevância', 'Menor preço', 'Maior avaliação']"
            size="sm"
            class="w-40"
          />
        </div>
      </div>

      <!-- Cards List -->
      <div class="space-y-4">
        <AppUiCardFreelancer v-for="i in 5" :key="i" />
      </div>
    </main>
  </AppLayoutLargeWrapper>
</template>
