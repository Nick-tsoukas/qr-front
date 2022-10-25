<template>
  <div>
    <section class="container mx-auto">
      <Hero class="mb-12" />
    </section>
    <section class="container mx-auto md:flex md:justify-between">
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
        subTitle="Get Social"
      />
      <Card
        heading="Custom Audio Player"
        :points="pointAudioPage"
        class="mb-12"
        sugTitle="Audio Player"
      />
      <Card
        heading="Create landing pages"
        :points="pointEvent"
        class="mb-12"
        subTitle="Events"
      />
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: {},
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
      type: 'social',
    }
  },
  async fetch() {
    this.data = await this.$strapi.find('test-data')
  },
}
</script>
