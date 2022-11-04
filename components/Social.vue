<template>
  <div class="fixed top-0 left-0 h-screen w-screen bg-white">
    <!-- header with close button  -->
    <div
      v-if="preview"
      class="bg-black text-white p-6 flex items-center justify-center"
      @click="closePreview"
    >
      <h1 class="text-center text-xl figlight">x close preview</h1>
    </div>
    <section v-if="create" class="mx-auto">
      <img
        v-if="image"
        height="350"
        :src="`http://localhost:1337${image}`"
        class="mx-auto"
      />
    </section>
    <section v-else class="mx-auto">
      <NuxtImg height="350" src="/band.jpg" class="mx-auto" />
    </section>
    <!-- Title  -->
    <section>
      <h1 class="text-3xl figbold my-6 pl-4">{{ headline }}</h1>
    </section>
    <section>
      <h1 class="text-lg figlight my-6 pl-4">{{ message }}</h1>
    </section>
    <!-- Buttons -->
    <section v-if="!create" class="container mx-auto">
      <a href="https://google.com">
        <SocialButtons
          icon="/facebook.svg"
          typeClass="facebook"
          class="mx-auto mb-6"
        />
      </a>
      <a href="https://google.com">
        <SocialButtons
          icon="/spotify.svg"
          typeClass="spotify"
          class="mx-auto mb-6"
      /></a>
      <a href="https://google.com">
        <SocialButtons
          icon="/messenger.svg"
          typeClass="facebook"
          class="mx-auto mb-6"
        />
      </a>
      <a href="https://google.com">
        <SocialButtons
          icon="/soundcloud.svg"
          typeClass="spotify"
          class="mx-auto mb-6"
        />
      </a>
    </section>
    <section v-else class="container mx-auto">
      <a
        v-for="button in buttons"
        :key="button.name"
        :href="`https://${button.link}`"
      >
        <SocialButtons
          :icon="`/${button.name}.svg`"
          :typeClass="button.name"
          class="mx-auto mb-6"
        />
      </a>
    </section>
  </div>
</template>

<script>
export default {
  props: {
    image: {
      type: String,
      default: () => {
        return ''
      },
    },
    create: {
      type: Boolean,
      default: () => {
        return true
      },
    },
    preview: {
      type: Boolean,
      default: () => {
        return false
      },
    },
    headline: {
      type: String,
      default: () => {
        return 'Fire'
      },
    },
    message: {
      type: String,
      default: () => {
        return ''
      },
    },
    buttons: {
      type: Object,
      default: () => {
        return {}
      },
    },
  },
  methods: {
    closePreview() {
      console.log('this should close the preview view')
      this.$emit('close')
    },
  },
}
</script>
