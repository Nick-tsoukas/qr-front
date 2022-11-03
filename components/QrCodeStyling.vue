<template>
  <div class="container mx-auto flex flex-col justify-center">
    <label for="color">Pick Color</label>
    <input type="color" v-model="color" @change="updateCode" />
    {{ color }} this is color
    <div class="mx-auto flex" id="qr-code" ref="qrCode"></div>
    <Button class="mt-6" text="Create QR" @click.native="createQr" />
  </div>
</template>

<script>
import QRCodeStyling from 'qr-code-styling'
import { uuid } from 'vue-uuid'
const NAMESPACE = '65f9af5d-f23f-4065-ac85-da725569fdcd'

export default {
  props: {
    dataQr: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      NAMESPACE,
      uuid: uuid.v1(),
      splashType: 'Social',
      user: {},
      chooseType: true,
      renderSplashForm: false,
      self: this,
      dataQrCode: 'http://localhost:3000/qr?id=true',
      color: '#000000',
      backgroundColor: '#ffffff00',
      qrCode: {},
      can: '',
    }
  },

  async mounted() {
    const user = await this.$strapi.findOne('users', this.$strapi.user.id)
    this.user = user
    this.qrCode = new QRCodeStyling({
      width: 300,
      height: 300,
      type: 'svg',
      data: this.dataQrCode,
      dotsOptions: {
        color: this.color,
        type: 'rounded',
      },
      backgroundOptions: {
        color: this.backgroundColor,
      },
      imageOptions: {
        crossOrigin: 'anonymous',
        margin: 20,
      },
    })
    this.qrCode.append(this.$refs.qrCode)
    console.log(this.qrCode)
  },
  methods: {
    createQr() {
      this.updateCode()
      this.$emit('createQr', this.qrCode)
    },
    downloadCode() {
      console.log('download code')
      this.qrCode.download()
    },
    renderForm() {
      this.chooseType = false
      this.renderSplashForm = true
    },
    setSplash(val) {
      this.splashType = val
    },
    updateCode() {
      if (!this.qrCode) {
        this.qrCode = new QRCodeStyling({
          width: 300,
          height: 300,
          type: 'svg',
          data: this.dataQrCode,
          dotsOptions: {
            color: this.color,
            type: 'rounded',
          },
          backgroundOptions: {
            color: this.backgroundColor,
          },
          imageOptions: {
            crossOrigin: 'anonymous',
            margin: 20,
          },
        })
        this.qrCode.append(this.$refs.qrCode)
      } else {
        this.qrCode.update({
          width: 300,
          height: 300,
          type: 'svg',
          data: this.dataQrCode,
          dotsOptions: {
            color: this.color,
            type: 'rounded',
          },
          backgroundOptions: {
            color: this.backgroundColor,
          },
          imageOptions: {
            crossOrigin: 'anonymous',
            margin: 20,
          },
        })
      }
    },
    saveQr() {
      // save splash forms vals and the qr options to the db
    },
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
