<script lang="ts" setup>
definePageMeta({ layout: "app" });

const experience = [
  {
    id: 1,
    role: "Desenvolvedor Frontend",
    company: "Empresa X",
    startYear: "2020",
    endYear: "2022",
    name: "E X",
  },
  {
    id: 2,
    role: "Desenvolvedor Fullstack",
    company: "Tech Solutions",
    startYear: "2022",
    endYear: "2024",
    name: "T S",
  },
  {
    id: 3,
    role: "Engenheiro de Software",
    company: "Startup Digital",
    startYear: "2024",
    endYear: "Presente",
    name: "S D",
  },
];
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileFreelancer>
      <!-- Cabeçalho da secção -->
      <div class="flex items-center justify-between mb-4">
        <div class="flex items-center gap-2">
          <h2 class="text-sm font-semibold text-gray-700 dark:text-gray-300 uppercase tracking-wide">
            Experiência
          </h2>
          <UBadge color="neutral" variant="subtle" size="xs">
            {{ experience.length }}
          </UBadge>
        </div>
      </div>

      <!-- Lista de experiências -->
      <ul class="divide-y divide-gray-100 dark:divide-gray-800">
        <AppUiCardExperience
          v-for="exp in experience"
          :key="exp.id"
          :start-year="exp.startYear"
          :end-year="exp.endYear"
          :company="exp.company"
          :role="exp.role"
          edit
        />
      </ul>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
