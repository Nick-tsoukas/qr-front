<template>
  <div>
    <section v-if="user">
      <h2 class="text-xl figbold my-6">Welcome</h2>
      <p>Username : {{ user.username }}</p>
      <p>Email : {{ user.email }}</p>
    </section>
    <section class="container mx-auto">
      <h2 class="text-xl figbold my-6">Create A QR</h2>
      <div v-if="chooseType">
        <p class="mb-6">Choose a type</p>
        <div
          class="flex flex-col mx-auto container items-center justify-center gap-4"
        >
          <div
            class="border-[1px] border-black rounded-md px-2 py-4 w-11/12 text-center"
            :class="splashType === 'Social' ? 'active' : ''"
            @click="setSplash('Social')"
          >
            Social Media Links
          </div>
          <div
            class="border-[1px] border-black rounded-md px-2 py-4 w-11/12 text-center"
            :class="splashType === 'Link' ? 'active' : ''"
            @click="setSplash('Link')"
          >
            Link To Website
          </div>
          <div
            class="border-[1px] border-black rounded-md px-2 py-4 w-11/12 text-center mt-6"
            @click="renderForm"
          >
            Continue
          </div>
        </div>
      </div>
      <div v-if="renderSplashForm">
        <component :is="`Create${splashType}`"></component>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      splashType: 'Social',
      user: {},
      chooseType: true,
      renderSplashForm: false,
    }
  },
  async mounted() {
    const user = await this.$strapi.findOne('users', this.$strapi.user.id)
    console.log(user, 'this is the user ')
    this.user = user
  },
  methods: {
    renderForm() {
      this.chooseType = false
      this.renderSplashForm = true
    },
    setSplash(val) {
      this.splashType = val
    },
  },
}
</script>

<style scoped>
.active {
  background: green;
  color: white;
}
</style>
