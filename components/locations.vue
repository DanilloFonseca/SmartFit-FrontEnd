<template>
    <div class="mx-auto mb-20 mt-4 grid w-[80%] max-w-[1050px] flex-1 grid-cols-1 gap-7 overflow-y-auto py-6 md:grid-cols-2 lg:grid-cols-3">
      <LocationItem
        v-for="location in locations?.locations"
        :key="location.id"
        :location="location"
      />
    </div>
  </template>
  
  <script setup lang="ts">
  import { useQuery } from '@tanstack/vue-query'
  import LocationItem from './location-card.vue'
  

  const { data: locations } = useQuery({
    queryKey: ['locations'],
    queryFn: async () => {
      const res = await fetch('https://test-frontend-developer.s3.amazonaws.com/data/locations.json')
      return res.json()
    }
  })
  </script>
  