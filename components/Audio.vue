<template>
  <div class="fixed top-0 left-0 h-screen w-screen bg-white">
    <!-- header with close button  -->
    <div
      class="bg-black text-white p-6 flex items-center justify-center"
      @click="closePreview"
    >
      <h1 class="text-center text-xl figlight">x close preview</h1>
    </div>
    <section class="mx-auto">
      <NuxtImg height="350" src="/band.jpg" class="mx-auto" />
    </section>
    <!-- Title  -->
    <section>
      <h1 class="text-3xl figbold text-center my-6">{{ headline }}</h1>
    </section>
    <section>
      <h1 class="text-lg figlight text-center my-6">{{ message }}</h1>
    </section>
    <!-- Buttons -->
    <section class="container mx-auto">
      <a href="https://google.com">
        <SocialButtons
          icon="/facebook.svg"
          typeClass="facebook"
          class="mx-auto"
        />
      </a>
      <a href="https://google.com">
        <SocialButtons icon="/spotify.svg" typeClass="spotify" class="mx-auto"
      /></a>
      <a href="https://google.com">
        <SocialButtons
          icon="/messenger.svg"
          typeClass="facebook"
          class="mx-auto"
        />
      </a>
      <a href="https://google.com">
        <SocialButtons
          icon="/soundcloud.svg"
          typeClass="spotify"
          class="mx-auto"
        />
      </a>
    </section>
  </div>
</template>

<script>
export default {
  props: {
    profileImg: {
      type: String,
      default: () => {
        return ''
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
        return 'Check us out on social media '
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
