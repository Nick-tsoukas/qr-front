<template>
  <div>
    <Nav v-if="$route.name !== 'qr'" />
    <Nuxt class="px-4" :class="{ 'pb-[120px]': $strapi.user }" />
    <!-- <Footer /> -->
  </div>
</template>

<script>
import Nav from '~/components/Nav.vue'
export default {
  components: { Nav },
}
</script>
