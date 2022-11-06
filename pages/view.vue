<template>
  <div>
    <section class="container">
      <div class="mx-auto flex justify-center" id="qr-code" ref="qrCode"></div>
      <section class="container mx-auto">
        <Button text="Download" class="mt-6" @click.native="download" />
      </section>
    </section>
  </div>
</template>

<script>
import QRCodeStyling from 'qr-code-styling'
export default {
  data() {
    return {
      qr: null,
      qrCode: null,
    }
  },
  async mounted() {
    const qr = await this.$strapi.findOne('qrs', this.$route.query.id)
    this.qr = qr
    this.qrCode = new QRCodeStyling(qr.qrOptions._options)
    this.qrCode.append(this.$refs.qrCode)
    console.log(this.qrCode)
  },
  methods: {
    download() {
      console.log('downloading ')
      this.qrCode.download({ name: 'qr', extension: 'svg' })
    },
  },
}
</script>

<style lang="scss" scoped></style>
