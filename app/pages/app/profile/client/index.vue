<script lang="ts" setup>
definePageMeta({ layout: "app" });
</script>

<template>
  <AppLayoutProfile>
    <AppLayoutProfileClient>
      <AppUiHeaderProfile>sobre mim</AppUiHeaderProfile>
      <div class="flex flex-col min-h-40 justify-between items-start">
        <p class="text-justify">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium
          voluptatem eveniet non, fugiat tempore perspiciatis nemo corrupti
          deserunt quaerat reprehenderit consequatur quidem vitae officia iusto
          delectus nihil necessitatibus magnam at.
        </p>
        <UModal>
          <UButton
            label="Editar"
            class="mt-6"
            color="neutral"
            variant="outline"
          />
          <template #header>
            <AppUiHeaderProfile> Editar sobre mim </AppUiHeaderProfile>
          </template>
          <template #body>
            <UForm>
              <UTextarea
                :rows="12"
                :cols="20"
                class="w-full"
                placeholder="lorem ipsum dolor sit amet adiscipling.."
              />
            </UForm>
          </template>
        </UModal>
      </div>
    </AppLayoutProfileClient>
  </AppLayoutProfile>
</template>
