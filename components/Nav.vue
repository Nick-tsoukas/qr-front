<template>
  <div>
    <div v-if="!isOpen" class="flex items-center h-[72px] px-4">
      <div class="flex-grow">
        <NuxtLink to="/"><nuxt-img src="/finallogo.svg" /></NuxtLink>
      </div>
      <div @click="toggleMenu">
        <nuxt-img src="/menu.svg" />
      </div>
    </div>
    <section
      v-else
      class="z-20 h-screen flex flex-col justify-around items-center w-screen bg-white fixed py-20 md:py-32 lg:py-40"
    >
      <div
        class="absolute top-4 right-4"
        style="font-size: 2em"
        @click="toggleMenu"
      >
        X
      </div>
      <div @click="toggleMenu">
        <NuxtLink class="figlight text-xl" to="/">Home</NuxtLink>
      </div>
      <div v-if="$strapi.user" @click="toggleMenu">
        <NuxtLink
          v-if="$strapi.user.band !== null"
          class="text-xl figlight"
          to="/profile"
          >Profile</NuxtLink
        >
      </div>

      <div v-if="$strapi.user">
        <div @click="logout">
          <NuxtLink class="figlight text-xl" to="/" @click="logout"
            >Logout
          </NuxtLink>
        </div>
      </div>
      <div v-if="!$strapi.user" @click="toggleMenu">
        <NuxtLink class="figlight text-xl" to="/signup" @click="toggleMenu"
          >signup</NuxtLink
        >
      </div>
      <div v-if="!$strapi.user" @click="toggleMenu">
        <NuxtLink class="figlight text-xl" to="/login" @click="toggleMenu"
          >Login</NuxtLink
        >
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mobile: true,
      isOpen: false,
    }
  },
  methods: {
    async logout() {
      console.log('logging out ')
      await this.$strapi.logout()

      this.isOpen = !this.isOpen
      const bodyElement = document.querySelectorAll('body')[0]
      if (this.isOpen) {
        bodyElement.style = 'overflow:hidden;'
      } else {
        bodyElement.style = ''
      }
    },
    toggleMenu() {
      this.isOpen = !this.isOpen
      const bodyElement = document.querySelectorAll('body')[0]
      if (this.isOpen) {
        bodyElement.style = 'overflow:hidden;'
      } else {
        bodyElement.style = ''
      }
    },
  },
}
</script>
