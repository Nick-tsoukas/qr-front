<template>
  <div>
    <section v-if="qr">
      <Social
        :image="qr.social.featImage ? qr.social.featImage.url : ''"
        :headline="qr.social.headline"
        :message="qr.social.message"
        :buttons="qr.social.buttons"
        @close="log"
      />
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      qr: null,
    }
  },
  async mounted() {
    try {
      const qr = await this.$strapi.findOne('qrs', this.$route.query.id)
      this.qr = qr
    } catch (error) {
      console.log(error)
    }
  },
}
</script>
