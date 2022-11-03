<template>
  <div>
    <Signup />
  </div>
</template>

<script>
export default {
  data() {
    return {}
  },
  mounted() {
    if (this.$strapi.user) {
      this.$router.push('/profile')
    }
  },
}
</script>

<style lang="scss" scoped></style>
