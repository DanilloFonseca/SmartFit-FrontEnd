<template>
  <div id="unidades" class="custom-shadow flex flex-col justify-start rounded bg-gray-100 p-3">
    <div :class="location.opened ? 'text-[#2FC022]' : 'text-red-500'" class="font-semibold">
      <strong>{{ location.opened ? 'Aberto' : 'Fechado' }}</strong>
    </div>

    <div class="text-2xl">
      <strong>{{ location.title }}</strong>
    </div>

    <div class="mt-2 text-gray-500" v-html="location.content"></div>

    <div class="my-4 flex h-[2px] w-full bg-gray-300"></div>

    <div class="flex flex-row items-center justify-around gap-4">
      <img
        v-if="location.mask === 'required'"
        :src="requiredMask"
        alt="Máscara obrigatória"
        width="50"
        height="80"
      />
      <img
        v-else-if="location.mask === 'recommended'"
        :src="recommendedMask"
        alt="Máscara recomendada"
        width="50"
        height="80"
      />

      <img
        v-if="location.towel === 'required'"
        :src="requiredTowel"
        alt="Toalha obrigatória"
        width="50"
        height="80"
      />
      <img
        v-else-if="location.towel === 'recommended'"
        :src="recommendedTowel"
        alt="Toalha recomendada"
        width="50"
        height="80"
      />

      <img
        v-if="location.fountain === 'partial'"
        :src="partialFountain"
        alt="Bebedouro parcial"
        width="50"
        height="80"
      />
      <img
        v-else-if="location.fountain === 'not_allowed'"
        :src="notAllowedFountain"
        alt="Bebedouro não permitido"
        width="50"
        height="80"
      />

      <img
        v-if="location.locker_room === 'allowed'"
        :src="allowedLocker"
        alt="Vestiário permitido"
        width="50"
        height="80"
      />
      <img
        v-else-if="location.locker_room === 'partial'"
        :src="partialLocker"
        alt="Vestiário parcial"
        width="50"
        height="80"
      />
      <img
        v-else-if="location.locker_room === 'closed'"
        :src="closedLocker"
        alt="Vestiário fechado"
        width="50"
        height="80"
      />
    </div>

    <div class="mt-4 grid grid-cols-2 gap-3">
      <div v-for="(schedule, index) in location.schedules" :key="index" class="flex flex-col">
        <p class="mb-1 text-xl font-semibold">
          <strong>{{ schedule.weekdays }}</strong>
        </p>
        <p class="text-sm">{{ schedule.hour }}</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { ILocation } from '@/types/location'

defineProps<{
  location: ILocation
}>()

import requiredMask from '@/assets/images/png/required-mask.png'
import recommendedMask from '@/assets/images/png/recommended-mask.png'

import requiredTowel from '@/assets/images/png/required-towel.png'
import recommendedTowel from '@/assets/images/png/recommended-towel.png'

import partialFountain from '@/assets/images/png/partial-fountain.png'
import notAllowedFountain from '@/assets/images/png/not_allowed-fountain.png'

import allowedLocker from '@/assets/images/png/allowed-lockerroom.png'
import partialLocker from '@/assets/images/png/partial-lockerroom.png'
import closedLocker from '@/assets/images/png/closed-lockerroom.png'
</script>
