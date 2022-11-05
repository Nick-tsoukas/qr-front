<template>
  <div>
    <div class="flex items-center justify-end h-[72px] px-4">
      <div class="flex-grow fixed top-6 left-4" @click="toggleMenu">
        <nuxt-img src="/menu.svg" />
      </div>
      <div>
        <NuxtLink to="/"><nuxt-img src="/finallogo.svg" /></NuxtLink>
      </div>
    </div>
    <div v-if="beenOpen">
      <section
        :class="{
          animate__slideInLeft: isOpen,
          animate__slideOutLeft: !isOpen,
        }"
        class="menuM bg-[#9b71fc] px-4 animate__animated z-20 h-screen flex flex-col w-screen fixed top-0 py-20 md:py-32 lg:py-40"
      >
        <div
          :class="{
            animate__slideInDown: isOpen,
            animate__slideOutUp: !isOpen,
          }"
          class="absolute top-0 left-0 animate__animated w-screen bg-black px-2 py-4"
          style="font-size: 2em"
          @click="toggleMenu"
        >
          <NuxtImg src="/closeicon.svg" class="whiteFilter" />
        </div>
        <div class="animate__animated">
          <div @click="toggleMenu">
            <div class="flex items-center py-6">
              <NuxtImg src="/home.svg" class="h-[30px] mr-4" />
              <NuxtLink class="figlight text-xl" to="/">Home</NuxtLink>
            </div>
          </div>
          <div v-if="$strapi.user" @click="toggleMenu">
            <div class="flex items-center py-6">
              <NuxtImg src="/profile.svg" class="h-[30px] mr-4" />
              <NuxtLink
                v-if="$strapi.user.band !== null"
                class="text-xl figlight"
                to="/profile"
                >Profile</NuxtLink
              >
            </div>
          </div>

          <div v-if="$strapi.user" @click="toggleMenu">
            <div class="flex items-center py-6">
              <NuxtImg src="/add.svg" class="h-[30px] mr-4" />
              <NuxtLink class="figlight text-xl" to="/create">Create </NuxtLink>
            </div>
          </div>

          <div v-if="$strapi.user">
            <div @click="logout">
              <div class="flex items-center py-6">
                <NuxtImg src="/logout.svg" class="h-[30px] mr-4" />
                <NuxtLink class="figlight text-xl" to="/" @click="logout"
                  >Logout
                </NuxtLink>
              </div>
            </div>
          </div>
          <div v-if="!$strapi.user" @click="toggleMenu">
            <div class="flex items-center py-6">
              <NuxtImg src="/profile.svg" class="h-[30px] mr-4" />
              <NuxtLink
                class="figlight text-xl"
                to="/signup"
                @click="toggleMenu"
                >Signup</NuxtLink
              >
            </div>
          </div>
          <div v-if="!$strapi.user" @click="toggleMenu">
            <div class="flex items-center py-6">
              <NuxtImg src="/profile.svg" class="h-[30px] mr-4" />
              <NuxtLink class="figlight text-xl" to="/login" @click="toggleMenu"
                >Login</NuxtLink
              >
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mobile: true,
      isOpen: true,
      beenOpen: true,
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
      if (this.beenOpen === false) {
        this.beenOpen = true
      }
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

<style scoped>
.animate__animated {
  --animate-duration: 0.3s;
}

.whiteFilter {
  filter: invert(100%) sepia(100%) saturate(0%) hue-rotate(1deg)
    brightness(103%) contrast(103%);
}
</style>
