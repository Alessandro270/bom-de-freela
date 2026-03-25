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
      <AppUiHeaderProfile class="flex justify-between">
        <span>Experiencia</span>
        <span class="text-slate-400">(5)</span>
      </AppUiHeaderProfile>
      <ul class="*:not-last:border-b *:not-last:border-slate-700">
        <AppUiCardExperience
          v-for="exp in experience"
          :key="exp.id"
          :start-year="exp.startYear"
          :end-year="exp.endYear"
          :company="exp.company"
          :role="exp.role"
        />
      </ul>
    </AppLayoutProfileFreelancer>
  </AppLayoutProfile>
</template>
