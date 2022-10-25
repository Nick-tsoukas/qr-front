<template>
  <div class="flex flex-col min-h-[500px] mx-auto w-full">
    <div>
      <h2 class="px-4 text-xl bg-[#1B2430] text-white py-6 rounded-lg fig">
        {{ heading }}
      </h2>
    </div>
    <div>
      <div class="py-6 bg-gray-50 rounded-lg my-4">
        <nuxt-img src="/phone.svg" class="h-[150px] mx-auto" />
      </div>
    </div>
    <div class="bg-[#1B2430] text-white py-8 px-4 rounded-lg min-h-[320px]">
      <h2 class="fig text-xl pb-2">{{ subTitle }}</h2>
      <ul class="text-gray-50">
        <li class="figlight" v-for="point in points" :key="point">
          {{ point }}
        </li>
      </ul>
      <div v-if="social">
        <div v-if="socialLinks.length > 0" class="grid grid-cols-4">
          <div
            v-for="link in socialLinks"
            :key="link"
            class="h-[30px] w-[30px] m-6"
          >
            <NuxtImg :src="link" />
          </div>
        </div>
      </div>
    </div>
    <div>
      <div class="mt-8">
        <Button
          class="bg-green-300 figbold"
          text-type="textType"
          text="Preview"
          @click.native="preview"
        />
      </div>
      <div class="mt-8">
        <Button
          class="bg-green-300 figbold"
          text-type="textType"
          text="Create QR"
          @click.native="preview"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    heading: {
      type: String,
      default: () => {
        return ''
      },
    },
    points: {
      type: Array,
      default: () => {
        return []
      },
    },
    social: {
      type: Boolean,
      default: () => {
        return false
      },
    },
    socialLinks: {
      type: Array,
      default: () => {
        return ['one']
      },
    },
    subTitle: {
      type: String,
      default: () => {
        'details'
      },
    },
    textType: {
      type: String,
      default: () => {
        return ''
      },
    },
    splashType: {
      type: String,
      default: () => {
        return ''
      },
    },
  },
  methods: {
    preview(val) {
      this.$emit('splashPreview', this.splashType)
    },
  },
}
</script>

<style scoped>
li {
  margin-bottom: 0.4rem;
}
</style>
