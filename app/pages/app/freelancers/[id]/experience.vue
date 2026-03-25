<script lang="ts" setup>
definePageMeta({ layout: "app" });

const experiences = reactive([
  {
    role: "Frontend Developer",
    company: "Tech Solutions",
    startYear: "2022",
    endYear: "2023",
  },
  {
    role: "Backend Developer",
    company: "Digital Systems",
    startYear: "2023",
    endYear: "2024",
  },
  {
    role: "Fullstack Developer",
    company: "Startup XYZ",
    startYear: "2024",
    endYear: "Presente",
  },
]);
</script>

<template>
  <AppLayoutFreelancer>
    <AppUiHeaderProfile class="flex justify-between">
      <span>experiencias</span>
      <span class="text-slate-500"> ({{ experiences.length }})</span>
    </AppUiHeaderProfile>
    <ul class="space-y-2 *:not-last:border-b *:not-last:border-slate-700">
      <AppUiCardExperience
        v-for="exp in experiences"
        :key="exp.company"
        :role="exp.role"
        :company="exp.company"
        :startYear="exp.startYear"
        :endYear="exp.endYear"
      />
    </ul>
  </AppLayoutFreelancer>
</template>
