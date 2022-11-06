<template>
  <div>
    <!-- Account message  -->
    <div
      class="mx-auto max-w-lg overflow-hidden rounded-lg shadow-lg lg:flex lg:max-w-none"
    >
      <div class="flex-1 bg-white px-6 py-8 lg:p-12">
        <h3
          class="text-2xl font-bold text-gray-900 sm:text-3xl sm:tracking-tight"
        >
          Free Membership
        </h3>
        <p class="mt-6 text-base text-gray-500">
          Upgrade and cancel at any time
        </p>
        <div class="mt-8">
          <div class="flex items-center">
            <h4
              class="flex-shrink-0 bg-white pr-4 text-base font-semibold text-green-400"
            >
              What's included
            </h4>
            <div class="flex-1 border-t-2 border-gray-200" />
          </div>
          <ul
            v-if="showFeatures"
            role="list"
            class="mt-8 space-y-5 lg:grid lg:grid-cols-2 lg:gap-x-8 lg:gap-y-5 lg:space-y-0"
          >
            <li
              v-for="feature in includedFeatures"
              :key="feature"
              class="flex items-start lg:col-span-1"
            >
              <div class="flex-shrink-0">
                <NuxtImg src="/add.svg" class="h-5 w-5" aria-hidden="true" />
              </div>
              <p class="ml-3 text-sm text-gray-700">{{ feature }}</p>
              <div></div>
            </li>
          </ul>
          <div
            v-if="showFeatures"
            class="flex w-[160px] items-center justify-center rounded-md border border-black px-2 py-2 text-base fig hover:['#9b71fc'] md:py-4 md:px-10 md:text-lg mt-6"
            @click="showFeatures = false"
          >
            <div class="flex items-center">
              <img src="/close.svg" alt="" class="h-[10px] mr-4" />
              <p>Show Less</p>
            </div>
          </div>
          <div
            v-else
            class="flex w-[160px] items-center justify-center rounded-md border border-black px-2 py-2 text-base fig hover:['#9b71fc'] md:py-4 md:px-10 md:text-lg mt-6"
            @click="showFeatures = true"
          >
            <div class="flex items-center">
              <img src="/close.svg" alt="" class="h-[10px] mr-4" />
              <p>Show More</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- qrs -->
    <h2 class="figbold my-4">Your Qrs</h2>
    <section class="rounded-sm">
      <!-- Header of qr list -->
      <div class="flex bg-black text-white px-2 py-1 items-center">
        <p class="w-[25%]">Name</p>
        <div class="flex justify-end w-[75%]">
          <p class="w-[25%] p-4">Link</p>
          <p class="w-[25%] p-4">View</p>
          <p class="w-[25%] p-4">Edit</p>
        </div>
        <hr />
      </div>
      <section class="" v-if="qrs.length > 0">
        <div
          v-for="qr in qrs"
          :key="qr.name"
          class="flex px-2 py-4 striped tableContainer items-center shadow-sm"
        >
          <p class="w-[25%]">{{ qr.name }}</p>
          <div class="flex justify-end items-center w-[75%]">
            <div class="w-[25%] p-4">
              <NuxtLink
                :to="`qr${qr.qrOptions.data.substring(
                  qr.qrOptions.data.indexOf('?'),
                  qr.qrOptions.data.length
                )}`"
              >
                <img class="w-[30px]" src="/linkicon.svg" />
              </NuxtLink>
            </div>
            <div class="w-[25%] p-4">
              <NuxtLink :to="`/view?id=${qr.id}`">
                <img class="w-[25px]" src="/viewicon.svg" />
              </NuxtLink>
            </div>
            <div class="w-[25%] p-4">
              <NuxtLink :to="`/edit?id=${qr.id}`">
                <img class="w-[25px]" src="/editicon.svg" />
              </NuxtLink>
            </div>
          </div>
        </div>
      </section>
      <section
        v-else
        class="border-l-[1px] border-r-[1px] border-b-[1px] border-black p-10 rounded-b-md"
      >
        <p class="text-center text-gray-500 figlight">No Qrs ...</p>
      </section>
    </section>
    <!-- Create Button here -->
    <section class="mt-6">
      <div class="rounded-md shadow bg-black">
        <nuxt-link
          to="/create"
          class="flex w-full items-center justify-center rounded-md border border-transparent bg-black px-8 py-3 text-base fig text-[#00FFD7] hover:['#9b71fc'] md:py-4 md:px-10 md:text-lg"
          ><div class="flex items-center">
            <img src="/add.svg" alt="" class="whiteFilter h-[20px] mr-4" />
            <p>Create Code</p>
          </div></nuxt-link
        >
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      qrs: [],
      includedFeatures: [
        '5 free dynamic QR Codes',
        'Unlimited edits',
        'Access to all our landing pages',
        'Full Support',
      ],
      showFeatures: true,
    }
  },
  async mounted() {
    if (!this.$strapi.user) {
      this.$router.push('/login')
    }
    const qrs = await this.$strapi.find('qrs', {
      users_permissions_user: this.$strapi.user.id,
    })
    this.qrs = qrs
  },
}
</script>

<style scoped>
/* colors #9b71fc purple  ... green #03d3aa */
.striped:nth-child(odd) {
  background: #f8f8f8;
}

.striped:nth-child(even) {
  background: white;
}
.tableContainer {
  border-left: 1px solid rgba(0, 0, 0, 0.222);
  border-right: 1px solid rgba(0, 0, 0, 0.222);
}
.tableContainer:last-child {
  border-bottom: 1px solid rgba(0, 0, 0, 0.222);
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
}
.whiteFilter {
  filter: invert(100%) sepia(100%) saturate(0%) hue-rotate(1deg)
    brightness(103%) contrast(103%);
}
</style>
