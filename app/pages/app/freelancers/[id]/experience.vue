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
    <!-- Section Header -->
    <div class="flex items-center gap-2 mb-4">
      <h2
        class="text-sm font-semibold text-gray-700 dark:text-gray-300 uppercase tracking-wide"
      >
        Experiência
      </h2>
      <UBadge color="neutral" variant="subtle" size="xs">{{
        experiences.length
      }}</UBadge>
    </div>

    <!-- Experience List -->
    <ul class="divide-y divide-gray-100 dark:divide-gray-800">
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
