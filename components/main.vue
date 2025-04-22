<template>
  <main class="mx-auto w-[80%] max-w-[1050px] flex-1 overflow-y-auto py-6">
    <div>
      <div class="text-4xl font-semibold">
        <h1>REABERTURA</h1>
        <h1>SMART FIT</h1>
      </div>
      <p class="mt-4">
        O horário de funcionamento das nossas unidades está seguindo os decretos de cada município.
        Por isso, confira aqui se a sua unidade está aberta e as medidas de segurança que estamos
        seguindo
      </p>
    </div>

    <div class="mt-6 rounded-lg border-4 p-4 text-lg text-gray-500">
      <div class="flex flex-row items-center gap-3">
        <img src="/assets/images/png/icon-hour.png" alt="icon-hour" width="30" height="70" />

        <div>Horários</div>
      </div>

      <div class="mt-6 text-xl font-light">Qual período você deseja treinar?</div>
      <div class="my-4 flex h-[2px] w-full bg-gray-300"></div>

      <div class="my-3 flex flex-col">
        <div v-for="period in periods" :key="period.value" class="my-1 flex-col">
          <label class="flex flex-row justify-between gap-2">
            <div class="flex flex-row gap-2">
              <input type="radio" :value="period.value" name="periodo" />
              <div>{{ period.label }}</div>
            </div>
            <div class="mr-2">{{ period.time }}</div>
          </label>
          <div class="mt-[10px] flex h-[2px] w-full bg-gray-300"></div>
        </div>
        <div class="mt-7 flex items-center justify-between text-black">
          <label class="flex items-center">
            <input type="checkbox" name="mostra-unidades-fechadas" />
            <p class="ml-2">Exibir Unidades Fechadas</p>
          </label>
          <div class="mr-2">
            Resultados Encontrados: <strong>{{ Quantidade }}</strong>
          </div>
        </div>
        <div class="mb-2 mt-7 flex items-center justify-center gap-4">
          <button
            class="flex h-16 w-64 flex-col items-center justify-center gap-1 rounded bg-[#FFB612] text-center font-semibold text-black hover:opacity-80 md:h-12 md:flex-row"
          >
            <div>ENCONTRAR UNIDADE</div>
          </button>
          <button
            class="flex h-12 w-64 items-center justify-center rounded border text-center font-semibold text-black hover:bg-gray-50"
          >
            <div>LIMPAR</div>
          </button>
        </div>
      </div>
    </div>
    <div
      class="mt-10 grid grid-cols-1 gap-10 bg-gray-100 p-3 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4"
    >
      <div v-for="(card, index) in cards" :key="index" class="flex flex-col items-center gap-3">
        <div>
          <strong>{{ card.title }}</strong>
        </div>
        <div class="flex flex-row items-center justify-center gap-3">
          <div
            v-for="(item, i) in card.items"
            :key="i"
            class="flex flex-col items-center justify-center"
          >
            <img :src="item.src" :alt="item.label" width="50" height="80" />
            <p>{{ item.label }}</p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import requiredMask from '@/assets/images/png/required-mask.png'
import recommendedMask from '@/assets/images/png/recommended-mask.png'
import requiredTowel from '@/assets/images/png/required-towel.png'
import recommendedTowel from '@/assets/images/png/recommended-towel.png'
import partialFountain from '@/assets/images/png/partial-fountain.png'
import notAllowedFountain from '@/assets/images/png/not_allowed-fountain.png'
import allowedLockerroom from '@/assets/images/png/allowed-lockerroom.png'
import partialLockerroom from '@/assets/images/png/partial-lockerroom.png'
import closedLockerroom from '@/assets/images/png/closed-lockerroom.png'

export default {
  data() {
    return {
      periods: [
        {
          label: 'Manhã',
          value: 'manha',
          time: 'Das 06:00 às 12:00',
        },
        {
          label: 'Tarde',
          value: 'tarde',
          time: 'Das 12:00 às 18:00',
        },
        {
          label: 'Noite',
          value: 'noite',
          time: 'Das 18:00 às 23:00',
        },
      ],
      Quantidade: 10,
      cards: [
        {
          title: 'Máscara',
          items: [
            { src: requiredMask, label: 'Obrigatório' },
            { src: recommendedMask, label: 'Recomendado' },
          ],
        },
        {
          title: 'Toalha',
          items: [
            { src: requiredTowel, label: 'Obrigatório' },
            { src: recommendedTowel, label: 'Recomendado' },
          ],
        },
        {
          title: 'Bebedouro',
          items: [
            { src: partialFountain, label: 'Parcial' },
            { src: notAllowedFountain, label: 'Proibido' },
          ],
        },
        {
          title: 'Vestiários',
          items: [
            { src: allowedLockerroom, label: 'Liberado' },
            { src: partialLockerroom, label: 'Parcial' },
            { src: closedLockerroom, label: 'Fechado' },
          ],
        },
      ],
    }
  },
  name: 'Main',
}
</script>
