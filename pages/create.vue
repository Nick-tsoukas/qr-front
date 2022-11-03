<template>
  <div>
    <!-- Create Qr (pick type) Section  -->
    <section class="container mx-auto">
      <h2 class="text-xl figbold my-2">Create A QR</h2>
      <div
        v-if="chooseType"
        class="flex flex-col justify-center items-center gap-6 md:flex-row"
      >
        <!-- Card One Social  -->
        <div class="max-w-sm rounded-md overflow-hidden shadow-lg">
          <div class="p-6 bg-gray-50">
            <img
              class="w-full max-h-[200px]"
              src="/phone.svg"
              alt="Sunset in the mountains"
            />
          </div>
          <div class="px-6 py-4">
            <div class="font-bold text-xl mb-2">Socia Media Landing Page</div>
            <p class="text-gray-700 text-base">
              List all your social media links, create a message with headline ,
              and add a featured image
            </p>
          </div>
          <div class="px-6 pt-4 pb-2 flex justify-start">
            <Button
              text="Preview"
              class="mr-4 flex-grow"
              @click.native="setPreview('Social')"
            />
            <Button
              text="Create Code"
              class="flex-grow"
              @click.native="renderForm('Social')"
            />
          </div>
        </div>
        <!-- Card Two -->
        <div class="max-w-sm rounded-md overflow-hidden shadow-lg">
          <div class="p-6 bg-gray-50">
            <img
              class="w-full max-h-[200px]"
              src="/phone.svg"
              alt="Sunset in the mountains"
            />
          </div>
          <div class="px-6 py-4">
            <div class="font-bold text-xl mb-2">Link to any content</div>
            <p class="text-gray-700 text-base">
              Add a link to anything on the web. Link to an eventpage, website,
              social media post, ect
            </p>
          </div>
          <div class="px-6 pt-4 pb-2 flex justify-start">
            <Button
              text="Preview"
              class="mr-4 flex-grow"
              @click.native="setPreview('Social')"
            />
            <Button
              text="Create Code"
              class="flex-grow"
              @click.native="renderForm('Social')"
            />
          </div>
        </div>
      </div>
      <div v-if="renderSplashForm">
        <keep-alive>
          <component :create="false" :is="`Create${splashType}`"></component>
        </keep-alive>
      </div>
    </section>
    <!-- This is the active class css   -->
    <!--  :class="splashType === 'Social' ? 'active' : ''" -->
    <component
      :preview="true"
      :is="previewComponent"
      v-if="preview"
      @close="closePre"
    ></component>
  </div>
</template>

<script>
export default {
  data() {
    return {
      splashType: 'Social',
      user: {},
      chooseType: true,
      renderSplashForm: false,
      preview: false,
      previewComponent: 'Social',
    }
  },

  async mounted() {
    const user = await this.$strapi.findOne('users', this.$strapi.user.id)
    this.user = user
  },
  methods: {
    renderForm(val) {
      this.splashType = val
      this.chooseType = false
      this.renderSplashForm = true
    },
    setSplash(val) {
      this.splashType = val
    },
    closePre() {
      console.log('this is the close pre ')
      this.preview = false
    },
    setPreview(val) {
      console.log('setPreview methods')
      this.previewType = val
      this.previewComponent = val
      this.preview = true
    },
  },
}
</script>

<style scoped>
.active {
  background: black;
  color: white;
}
</style>
