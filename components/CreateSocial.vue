<template>
  <section>
    <div v-if="!styleQr && !previewSplash">
      <div
        v-if="!image"
        class="sm:grid sm:grid-cols-3 sm:items-start sm:gap-4 sm:border-t sm:border-gray-200 sm:pt-5"
      >
        <label
          for="cover-photo"
          class="block text-sm font-medium text-gray-700 sm:mt-px sm:pt-2"
          >Set Featured Image
        </label>
        <div class="mt-1 sm:col-span-2 sm:mt-0">
          <div
            class="flex max-w-lg justify-center rounded-md border-2 border-dashed border-gray-300 px-6 pt-5 pb-6"
          >
            <div class="space-y-1 text-center">
              <svg
                class="mx-auto h-12 w-12 text-gray-400"
                stroke="currentColor"
                fill="none"
                viewBox="0 0 48 48"
                aria-hidden="true"
              >
                <path
                  d="M28 8H12a4 4 0 00-4 4v20m32-12v8m0 0v8a4 4 0 01-4 4H12a4 4 0 01-4-4v-4m32-4l-3.172-3.172a4 4 0 00-5.656 0L28 28M8 32l9.172-9.172a4 4 0 015.656 0L28 28m0 0l4 4m4-24h8m-4-4v8m-12 4h.02"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
              <div class="flex text-sm text-gray-600">
                <label
                  for="file-upload"
                  class="relative cursor-pointer rounded-md bg-white font-medium text-indigo-600 focus-within:outline-none focus-within:ring-2 focus-within:ring-indigo-500 focus-within:ring-offset-2 hover:text-indigo-500"
                >
                  <span v-if="!image">Upload a file</span>
                  <span v-if="image">Edit Image</span>
                  <input
                    id="file-upload"
                    name="file-upload"
                    type="file"
                    class="sr-only"
                    @change="preview($event.target.files[0])"
                  />
                </label>
                <p class="pl-1">or drag and drop</p>
              </div>
              <p class="text-xs text-gray-500">PNG, JPG, GIF up to 10MB</p>
            </div>
          </div>
        </div>
      </div>
      <!-- <div class="mt-1">
        <label for="title" class="block text-sm font-medium text-gray-700"
          >Featured Image
        </label>
        <input
          name="title"
          type="file"
          autocomplete="text"
          required=""
          class="block w-full appearance-none rounded-md border border-gray-300 px-3 py-2 placeholder-gray-400 shadow-sm focus:border-indigo-500 focus:outline-none focus:ring-indigo-500 sm:text-sm"
          @change="formValues.featImage = $event.target.files[0]"
        />
      </div> -->
      <div class="my-2" v-if="image">
        <img :src="image" alt="" class="mx-auto" />
        <label
          for="file-upload"
          class="relative cursor-pointer rounded-md bg-white font-medium text-indigo-600 focus-within:outline-none focus-within:ring-2 focus-within:ring-indigo-500 focus-within:ring-offset-2 hover:text-indigo-500"
        >
          <span v-if="image">Edit Image</span>
          <input
            id="file-upload"
            name="file-upload"
            type="file"
            class="sr-only"
            @change="preview($event.target.files[0])"
          />
        </label>
      </div>
      <div class="mt-1">
        <label for="title" class="block text-sm font-medium text-gray-700"
          >Title</label
        >
        <input
          v-model="formValues.title"
          name="title"
          type="text"
          autocomplete="text"
          required=""
          class="block w-full appearance-none rounded-md border border-gray-300 px-3 py-2 placeholder-gray-400 shadow-sm focus:border-indigo-500 focus:outline-none focus:ring-indigo-500 sm:text-sm"
        />
      </div>
      <div class="mt-1 mb-6">
        <label for="message" class="block text-sm font-medium text-gray-700"
          >Message</label
        >
        <input
          v-model="formValues.message"
          name="message"
          type="text"
          autocomplete="text"
          required=""
          class="block w-full appearance-none rounded-md border border-gray-300 px-3 py-2 placeholder-gray-400 shadow-sm focus:border-indigo-500 focus:outline-none focus:ring-indigo-500 sm:text-sm"
        />
      </div>
      <div class="mt-1">
        <label
          for="facebook"
          class="block text-sm font-medium text-gray-700 mb-4"
          >Facebook Link</label
        >
        <div class="flex">
          <nuxt-img src="/facebook.svg" height="30" width="30" class="mr-6" />
          <input
            v-model="formValues.buttons.facebook"
            name="facebook"
            type="text"
            placeholder="https:/facebook/youname"
            autocomplete="text"
            required=""
            class="block w-full appearance-none rounded-md border border-gray-300 px-3 py-2 placeholder-gray-400 shadow-sm focus:border-indigo-500 focus:outline-none focus:ring-indigo-500 sm:text-sm"
          />
        </div>
      </div>
      <div class="mt-1">
        <label
          for="spotify"
          class="block text-sm font-medium text-gray-700 my-4"
          >Spotify Link</label
        >
        <div class="flex">
          <nuxt-img src="/spotify.svg" height="30" width="30" class="mr-6" />
          <input
            v-model="formValues.buttons.spotify"
            name="spotify"
            type="text"
            placeholder="https:/spotify/yourband"
            autocomplete="text"
            required=""
            class="block w-full appearance-none rounded-md border border-gray-300 px-3 py-2 placeholder-gray-400 shadow-sm focus:border-indigo-500 focus:outline-none focus:ring-indigo-500 sm:text-sm"
          />
        </div>
      </div>

      <div class="mt-1">
        <label
          for="soundcloud"
          class="block text-sm font-medium text-gray-700 my-4"
          >Soundcloud Link</label
        >
        <div class="flex">
          <nuxt-img src="/soundcloud.svg" height="30" width="30" class="mr-6" />
          <input
            v-model="formValues.buttons.soundcloud"
            name="soundcloud"
            type="text"
            placeholder="https:/soundcloud/yourband"
            autocomplete="text"
            required=""
            class="block w-full appearance-none rounded-md border border-gray-300 px-3 py-2 placeholder-gray-400 shadow-sm focus:border-indigo-500 focus:outline-none focus:ring-indigo-500 sm:text-sm"
          />
        </div>
      </div>
      <Button text="next" class="mt-6" @click.native="previewSocial" />
      <Button text="next" class="mt-6" @click.native="next" />
    </div>
    <QrCodeStyling v-if="styleQr && !previewSplash" />
    <Social v-if="previewSplash" :image="image ? image : ''" @close="log" />
  </section>
</template>

<script>
export default {
  data() {
    return {
      formValues: {
        buttons: {},
        featImage: false,
      },
      image: false,
      title: 'Create Your Landing Page',
      styleQr: false,
      previewSplash: false,
    }
  },
  methods: {
    async next() {
      console.log('sending form')
      try {
        console.log(this.formValues.featImage, ' logging ')
        if (this.formValues.featImage) {
          const formData = new FormData()
          await formData.append('files', this.formValues.featImage)
          const [image] = await this.$strapi.create('upload', formData)
          this.image = image
          this.formValues.featImage = image
        }
        console.log(this.formValues)
        this.title = 'Style Your QR'
        this.styleQr = true
      } catch (error) {
        console.log(error)
      }
    },
    log() {
      this.previewSplash = false
    },
    setImage(event) {
      console.log(event.target.files, 'this is clicked ')
      this.formValues.file = event.target.files[0]
    },
    preview(val) {
      this.formValues.featImage = val
      this.image = URL.createObjectURL(val)
    },
    previewSocial() {
      this.previewSplash = true
    },
  },
}
</script>
