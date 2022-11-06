<template>
  <div>
    <div class="flex items-center justify-end h-[72px] px-4">
      <div
        class="flex-grow fixed top-6 left-4"
        :class="{ 'z-50': !isOpen }"
        @click="toggleMenu"
      >
        <nuxt-img src="/menu.svg" class="" />
      </div>
      <div>
        <NuxtLink to="/" class="blackNav"
          ><nuxt-img src="/finallogo.svg"
        /></NuxtLink>
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
          class="absolute top-0 left-0 animate__animated w-screen bg-black px-4 py-4"
          style="font-size: 2em"
          @click="toggleMenu"
        >
          <NuxtImg src="/closeicon.svg" class="whiteFilter h-[30px]" />
        </div>
        <div class="animate__animated">
          <div @click="toggleMenu">
            <NuxtLink class="figlight text-xl flex items-center py-6" to="/"
              ><NuxtImg
                src="/home.svg"
                class="h-[30px] mr-4"
                :class="{ greenIcon: $route.name === 'index' }"
              />
              <p>Home</p></NuxtLink
            >
          </div>
          <div v-if="$strapi.user" @click="toggleMenu">
            <NuxtLink
              class="figlight active text-xl flex items-center py-6"
              to="/profile"
              ><NuxtImg src="/profile.svg" class="h-[30px] mr-4 active" />
              <p>Profile</p></NuxtLink
            >
          </div>

          <div v-if="$strapi.user" @click="toggleMenu">
            <NuxtLink
              class="figlight active text-xl flex items-center py-6"
              to="/create"
              ><NuxtImg src="/add.svg" class="h-[30px] mr-4 active" />
              <p>Create</p></NuxtLink
            >
          </div>

          <div v-if="$strapi.user">
            <div @click="logout">
              <NuxtLink class="figlight text-xl flex items-center py-6" to="/"
                ><NuxtImg src="/logout.svg" class="h-[30px] mr-4" />
                <p>Logout</p></NuxtLink
              >
            </div>
          </div>
          <div v-if="!$strapi.user" @click="toggleMenu">
            <NuxtLink
              class="figlight active text-xl flex items-center py-6"
              to="/signup"
              ><NuxtImg src="/signup.svg" class="h-[30px] mr-4 active" />
              <p>Signup</p></NuxtLink
            >
          </div>
          <div v-if="!$strapi.user" @click="toggleMenu">
            <NuxtLink
              class="figlight active text-xl flex items-center py-6"
              to="/login"
              ><NuxtImg src="/profile.svg" class="h-[30px] mr-4 active" />
              <p>Login</p></NuxtLink
            >
          </div>
        </div>
      </section>
    </div>
    <!-- bottom nav bar -->
    <!-- <section
      v-if="!$strapi.user"
      class="w-screen bg-black flex justify-around fixed bottom-0 left-0 z-50 text-white py-2 shadow"
    >
      <NuxtLink class="flex items-center bottomBox active py-4" to="/">
        <img src="/home.svg" class="whiteFilter h-[25px] mr-4" alt="" />
        <p class="figlight">Home</p>
      </NuxtLink>
      <NuxtLink class="flex items-center bottomBox active py-4" to="/login">
        <img src="/profile.svg" class="whiteFilter h-[25px] mr-4" alt="" />
        <p class="figlight">Login</p>
      </NuxtLink>
      <NuxtLink class="flex items-center bottomBox py-4 active" to="/signup">
        <img src="/signup.svg" class="whiteFilter h-[25px] mr-4" alt="" />
        <p class="figligh">Signup</p>
      </NuxtLink>
    </section> -->
    <section
      class="w-screen animate__animated bg-[#4338CA] flex justify-around fixed bottom-0 left-0 z-50 text-white py-2 shadow"
      :class="{
        animate__slideInUp: $strapi.user,
        animate__slideOutDown: !$strapi.user,
      }"
    >
      <NuxtLink class="flex items-center bottomBox active py-4" to="/profile">
        <img src="/home.svg" class="whiteFilter h-[25px] mr-4" alt="" />
        <p class="figlight">Profile</p>
      </NuxtLink>
      <NuxtLink class="flex items-center bottomBox active py-4" to="/create">
        <img src="/profile.svg" class="whiteFilter h-[25px] mr-4" alt="" />
        <p class="figlight">Create QR</p>
      </NuxtLink>
      <NuxtLink
        class="flex items-center bottomBox py-4"
        to="/"
        @click.native="logoutBottom"
      >
        <img src="/logout.svg" class="whiteFilter h-[25px] mr-4" alt="" />
        <p class="figlight">Logout</p>
      </NuxtLink>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mobile: true,
      isOpen: false,
      beenOpen: false,
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
    async logoutBottom() {
      await this.$strapi.logout()
    },
    log() {
      console.log('hello you clicked me nav bar ')
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
a.nuxt-link-active {
  font-weight: bold;
}

a.active.nuxt-link-active > img {
  filter: invert(95%) sepia(22%) saturate(2706%) hue-rotate(85deg)
    brightness(110%) contrast(101%);
}
.greenIcon {
  filter: invert(95%) sepia(22%) saturate(2706%) hue-rotate(85deg)
    brightness(110%) contrast(101%);
}
</style>
