<template>
  <div>
    <Hero class="mb-12" />
    <Card heading="Create landing pages" :points="pointLanding" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: {},
      pointLanding: [
        'Create band profiles, venues, and bio pages',
        'Upload music and sell tracts',
        'Convert auido into NFTs',
      ],
    }
  },
  async fetch() {
    this.data = await this.$strapi.find('test-data')
  },
}
</script>
