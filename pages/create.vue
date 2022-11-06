<template>
  <div>
    <!-- Create Qr (pick type) Section  -->
    <section v-if="!preview" class="container mx-auto">
      <div v-if="chooseType">
        <Back />
        <h2 class="text-xl figbold my-4">Choose a QR Code type</h2>
      </div>
      <div
        v-if="chooseType"
        class="flex flex-col justify-center items-center gap-6 md:flex-row"
      >
        <!-- Card One Social  -->
        <div class="max-w-sm rounded-md overflow-hidden shadow-lg">
          <CardImage class="bg-[#00e7ff]" />
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
          <CardImage class="bg-[#67b99a]" />
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
        <!-- Card Three -->
        <div class="max-w-sm rounded-md overflow-hidden shadow-lg">
          <CardImage class="bg-[#aed9e0]" />
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
          <component
            :create="false"
            :is="`Create${splashType}`"
            @goBackFromSplash="
              {
                ;(renderSplashForm = false), (chooseType = true)
              }
            "
          ></component>
        </keep-alive>
      </div>
    </section>
    <!-- This is the active class css   -->
    <!--  :class="splashType === 'Social' ? 'active' : ''" -->
    <component
      :preview="true"
      headline="Fire"
      message="Thanks for checking us out on social media, please check back with us for our next show"
      :create="false"
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
    goBack() {
      this.renderSplashForm = false
      this.chooseType = true
    },
    goBackSplash() {
      this.renderSplashForm = false
    },

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
