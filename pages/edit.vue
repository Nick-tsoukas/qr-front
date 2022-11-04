<template>
  <div>
    <h1>This is the edit qr page</h1>
  </div>
</template>

<script>
export default {
  mounted() {
    console.log(this.$route.query.id)
  },
}
</script>
