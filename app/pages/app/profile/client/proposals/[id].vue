<script lang="ts" setup>
definePageMeta({ layout: "app" });

const proposals = [
  {
    id: 1,
    name: "Marcos Silva",
    sentAt: "23/03/2026",
    value: "320,000.00 KZ",
    status: null,
  },
  {
    id: 2,
    name: "Ana Ferreira",
    sentAt: "23/03/2026",
    value: "410,000.00 KZ",
    status: null,
  },
  {
    id: 3,
    name: "João Baptista",
    sentAt: "24/03/2026",
    value: "500,000.00 KZ",
    status: null,
  },
];

const statuses = ref<Record<number, "accepted" | "rejected" | null>>(
  Object.fromEntries(proposals.map((p) => [p.id, p.status])),
);
</script>

<template>
  <div
    class="font-google justify-center flex flex-col space-y-10 max-w-2/3 mx-auto"
  >
    <div class="w-full">
      <div class="space-y-2">
        <h1 class="text-2xl font-medium text-justify">
          Lorem ipsum, dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat.
        </h1>
        <div class="flex items-center gap-2">
          <UiRating :value="5" />
          <AppUiButtonDesc title="Avaliações" value="(5)" />
          <AppUiButtonDesc title="Postado em" value="23/03/2026" />
        </div>
      </div>

      <div class="mt-4 bg-slate-950 space-y-4 px-6 py-7 rounded-sm">
        <h2 class="text-xl uppercase font-medium flex justify-between">
          <span>Descrição</span>
          <span>500,000.00 kz</span>
        </h2>
        <p class="text-slate-300 text-justify">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illo at,
          ratione totam fugiat omnis nobis iste placeat, quidem soluta quia,
          voluptate nam ipsam quisquam porro voluptas possimus dolore quasi ea!
        </p>
        <div class="flex flex-col space-y-2">
          <AppUiButtonDesc
            title="Categoria"
            value="Desenvolvimento de Software"
          />
          <AppUiButtonDesc title="Subcategoria" value="Desenvolvimento Web" />
          <AppUiButtonDesc title="Prazo de entrega" value="30/03/2026" />
        </div>
        <div class="flex items-end justify-between">
          <div class="space-y-3">
            <span class="text-slate-100 inline-block font-medium"
              >Habilidades necessárias</span
            >
            <div class="space-x-3">
              <AppUiButtonTag>python</AppUiButtonTag>
              <AppUiButtonTag>javascript</AppUiButtonTag>
              <AppUiButtonTag>java</AppUiButtonTag>
            </div>
          </div>

          <AppUiButtonSideSecondary> Editar </AppUiButtonSideSecondary>
        </div>
      </div>
    </div>
    <div class="grid gap-6 grid-cols-2">
      <AppUiCardFreelancerProposal
        v-for="proposal in proposals"
        :key="proposal.id"
        :name="proposal.name"
        :sent-at="proposal.sentAt"
        :value="proposal.value"
      >
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Eveniet ut
        ullam, et optio enim qui porro commodi minima reprehenderit nam corrupti
        officia. Repellat, rem nulla. Veniam ex error quasi. Ipsam.
      </AppUiCardFreelancerProposal>
    </div>
  </div>
</template>
