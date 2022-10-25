<template>
  <div>
    <section class="container mx-auto">
      <Hero class="mb-12" />
    </section>
    <section
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
      />
      <Card
        heading="Audio Player"
        :points="pointAudioPage"
        class="mb-12"
        sugTitle="Audio Player"
        textType="Audio"
      />
      <Card
        heading="Event Page"
        :points="pointEvent"
        class="mb-12"
        subTitle="Events"
        textType="Event"
      />
      <Card
        heading="Website Link"
        :points="pointEvent"
        class="mb-12"
        subTitle="Link"
        textType="Link"
      />
      <Card
        heading="Band Profile"
        :points="pointBand"
        class="mb-12"
        subTitle="Band Profile"
        textType="Band Profile"
      />
      <Card
        heading="Share Contact"
        :points="pointContact"
        class="mb-12"
        subTitle="Share Contact"
        textType="Share Contact "
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
    }
  },
  async fetch() {
    this.data = await this.$strapi.find('test-data')
  },
}
</script>
