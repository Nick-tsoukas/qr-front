<template>
  <div>
    <Login v-if="login" @createComp="setCreate" />
    <Signup v-else @createComp="setLogin" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      login: true,
    }
  },
  mounted() {
    if (this.$strapi.user) {
      this.$router.push('/profile')
    }
  },
  methods: {
    setCreate() {
      this.login = false
    },
    setLogin() {
      console.log('this should show th login')
      this.login = true
    },
  },
}
</script>

<style lang="scss" scoped></style>
