<template>
  <div>this is the logout page</div>
</template>

<script>
export default {
  mounted() {
    if (this.$strapi.user) {
      this.$router.push('/profile')
    }
  },
}
</script>

<style lang="scss" scoped></style>
