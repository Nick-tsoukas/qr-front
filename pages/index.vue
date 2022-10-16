<template>
  <div>
    <Hero />
    {{ data }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: {},
    }
  },
  async fetch() {
    this.data = await this.$strapi.find('test-data')
  },
}
</script>
