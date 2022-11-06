<template>
  <div>
    <section class="container" v-show="qr">
      <div class="mx-auto flex justify-center" id="qr-code" ref="qrCode"></div>
    </section>
    <div class="flex gap-6">
      <div
        class="flex w-[160px] items-center justify-center rounded-md border border-black px-2 py-2 text-base fig hover:['#9b71fc'] md:py-4 md:px-10 md:text-lg mt-6"
      >
        <div class="flex items-center">
          <img src="/editicon.svg" alt="" class="h-[10px] mr-4" />
          <p>Edit Style</p>
        </div>
      </div>
      <div
        class="flex w-[160px] items-center justify-center rounded-md border border-black px-2 py-2 text-base fig hover:['#9b71fc'] md:py-4 md:px-10 md:text-lg mt-6"
      >
        <div to="/profile" class="flex items-center" @click="deleteQR">
          <img src="/editicon.svg" alt="" class="h-[10px] mr-4" />
          <p>Delete Code</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import QRCodeStyling from 'qr-code-styling'
export default {
  data() {
    return {
      qr: null,
      qrCode: null,
      loading: false,
    }
  },

  async mounted() {
    const qr = await this.$strapi.findOne('qrs', this.$route.query.id)
    this.loading = false
    this.qr = qr
    this.qrCode = new QRCodeStyling(qr.qrOptions._options)
    this.qrCode.append(this.$refs.qrCode)
  },
  methods: {
    async deleteQR() {
      await this.$strapi.delete('qrs', this.qr.id)
      this.$router.push('/profile')
    },
  },
}
</script>

<style lang="scss" scoped></style>
