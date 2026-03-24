<script lang="ts" setup>
defineProps<{
  title: string;
  acceptedAt: string;
  deadline: string;
  clientName: string;
  status: "em_progresso" | "concluido";
  id: string | number;
}>();
</script>

<template>
  <div class="py-4 flex items-startjustify-between">
    <div class="space-y-2 flex-1 min-w-0">
      <h3 class="text-slate-100 font-bold text-sm uppercase leading-snug">
        {{ title }}
      </h3>
      <div class="flex space-x-4 items-center">
        <AppUiButtonSmallAvatar :name="clientName" />

        <div>
          <span class="text-slate-200 text-sm font-medium">
            {{ clientName }}
          </span>
          <div class="space-x-4">
            <span class="text-slate-400 text-xs italic">
              aceite em:
              <span class="text-slate-200 not-italic font-medium">
                {{ acceptedAt }}
              </span>
            </span>
            <span class="text-slate-400 text-xs italic">
              deadline:
              <span class="text-slate-200 not-italic font-medium">
                {{ deadline }}
              </span>
            </span>
          </div>
        </div>
      </div>
    </div>

    <div class="text-right h-18 flex flex-col justify-between">
      <p class="text-slate-400 text-xs italic">
        estado:
        <span
          class="not-italic font-medium"
          :class="status === 'concluido' ? 'text-purple-500' : 'text-slate-400'"
        >
          {{ status === "concluido" ? "Concluído" : "Em progresso" }}
        </span>
      </p>
      <NuxtLink
        :to="`/app/profile/freelancer/projects/${id}`"
        class="text-xs text-slate-300 hover:text-white transition-colors"
      >
        Ver detalhes
      </NuxtLink>
    </div>
  </div>
</template>
