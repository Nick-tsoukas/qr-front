<template>
  <section>
    <h2 class="figbold text-xl text-center">Create All Your Links Page</h2>
    <div>
      <div class="mt-1">
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
      </div>
      <div class="my-2" v-if="image">
        <p>image is set</p>
        <img :src="`http://localhost:1337${image.url}`" alt="" />
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
      <div @click="submit">Submit</div>
    </div>
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
    }
  },
  methods: {
    async submit() {
      console.log('sending form')
      try {
        if (this.formValues.featImage) {
          const formData = new FormData()
          await formData.append('files', this.formValues.featImage)
          const [image] = await this.$strapi.create('upload', formData)
          this.image = image
          this.formValues.featImage = image
        }
        console.log(this.formValues)
      } catch (error) {
        console.log(error)
      }
    },
    log() {
      console.log(this.formValues, 'this is the form values ')
    },
    setImage(event) {
      console.log(event.target.files, 'this is clicked ')
      this.formValues.file = event.target.files[0]
    },
  },
}
</script>
