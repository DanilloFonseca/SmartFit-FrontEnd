<template>
  <div class="flex min-h-screen flex-col items-center">
    <Header />
    <Main />
    <ClientOnly>
      <Locations />
    </ClientOnly>
    <Footer />
  </div>
</template>

<script>
import Header from '~/components/header.vue'
import Footer from '~/components/footer.vue'
import Main from '~/components/main.vue'
import Locations from '@/components/locations.vue'
import { ClientOnly } from '#components'
</script>
