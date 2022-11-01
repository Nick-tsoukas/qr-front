<template>
  <div>
    <div v-if="!preview && !signup && !login">
      <section class="container mx-auto">
        <!-- <Hero class="mb-12" /> -->
        <HeroAlt />
      </section>
      <!-- <section
        class="container mx-auto md:grid md:grid-cols-3 md:justify-between md:gap-14"
      >
        <Card
          heading="All Social Links"
          :points="pointLandingSocial"
          class="mb-12"
          :social="true"
          :socialLinks="[
            '/youtube.svg',
            '/whatsapp.svg',
            '/snapchat.svg',
            '/spotify.svg',
            '/soundcloud.svg',
            'facebook.svg',
            'messenger.svg',
            'flickr.svg',
          ]"
          subTitle="Social"
          textType="Social"
          splashType="Social"
          @splashPreview="setPreview"
          @createCode="create"
        />
        <Card
          heading="Audio Player"
          :points="pointAudioPage"
          class="mb-12"
          sugTitle="Audio Player"
          textType="Audio"
          splashType="Audio"
          @splashPreview="setPreview"
          @createCode="create"
        />
        <Card
          heading="Event Page"
          :points="pointEvent"
          class="mb-12"
          subTitle="Events"
          textType="Event"
          splashType="Event"
          @splashPreview="setPreview"
          @createCode="create"
        />
        <Card
          heading="Website Link"
          :points="pointEvent"
          class="mb-12"
          subTitle="Link"
          textType="Link"
          splashType="Link"
          @splashPreview="setPreview"
          @createCode="create"
        />
        <Card
          heading="Band Profile"
          :points="pointBand"
          class="mb-12"
          subTitle="Band Profile"
          textType="Band Profile"
          splashType="Band"
          @splashPreview="setPreview"
          @createCode="create"
        />
        <Card
          heading="Share Contact"
          :points="pointContact"
          class="mb-12"
          subTitle="Share Contact"
          textType="Share Contact "
          splashType="Contact"
          @splashPreview="setPreview"
          @createCode="create"
        />
      </section> -->
    </div>
    <Signup
      @closeSignup="closeSignup"
      @openLogin="openLogin"
      v-if="signup"
      :home="true"
      :splashType="splashType"
    />
    <Login
      @closeLogin="closeLogin"
      v-if="login"
      :home="true"
      :splashType="splashType"
    />
    <component
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
      data: {},
      signup: false,
      login: false,
      preview: false,
      previewComponent: 'Social',
      pointLandingSocial: [
        'List all your social media links ',
        'Facebook Twitch Tiktoc Snap ...',
      ],
      pointAudioPage: [
        'Create a alubm or track list ',
        'Upload you auidio files',
        'Custom Audio player ',
      ],
      pointEvent: [
        'List an upcoming show',
        'Add a tour and list shows  ',
        'Load your event poster or image ',
        'Create a qr that links to the ticket pages too!',
      ],
      pointContact: [
        'Share Contact Info Easy',
        'Use NFC to send your contact info ',
        'Get link to your own contact page ',
        'Show your code with your contact info with you mobile device ',
      ],
      pointBand: [
        'Band Profile Landing Page ',
        'Customize and create a landing page for your band',
        'Add custom links to your page ',
        'List Upcoming shows and more',
      ],
      type: 'social',
      splashType: '',
    }
  },
  methods: {
    create(val) {
      console.log(val, 'this is val')
      this.splashType = val
      if (!this.$strapi.user) {
        this.signup = true
      }
    },
    closeSignup() {
      console.log('this is the close signup ')
      this.signup = false
      this.login = false
    },
    openLogin() {
      console.log('this is the close signup ')
      this.signup = false
      this.login = true
    },
    closeLogin() {
      console.log('this is the close signup ')
      this.signup = false
      this.login = false
    },
    setPreview(val) {
      this.previewType = val
      this.previewComponent = val
      this.preview = true
    },
    closePre() {
      console.log('this is the close pre ')
      this.preview = false
    },
  },
}
</script>
