<template>
  <div>
    <div>
      <NuxtLink to="/create">
        <div class="flex items-center border-[1px] border-black">
          <img src="/addicon.svg" alt="" />
          <p class="text-lg figbold">Add QR Code</p>
        </div>
      </NuxtLink>
    </div>
    <h2 class="figbold my-4">Your Qrs</h2>
    <section class="rounded-sm">
      <!-- Header of qr list -->
      <div class="flex bg-black text-white px-2 py-4">
        <p class="w-[25%]">Name</p>
        <div class="flex justify-end w-[75%]">
          <p class="w-[25%] p-4">Link</p>
          <p class="w-[25%] p-4">View</p>
          <p class="w-[25%] p-4">Edit</p>
        </div>
        <hr />
      </div>
      <section v-if="qrs.length > 0">
        <div v-for="qr in qrs" :key="qr.name" class="flex px-2 py-4 striped">
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
  </div>
</template>

<script>
export default {
  data() {
    return {
      qrs: [],
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
.striped:nth-child(odd) {
  background: #f8f8f8;
}

.striped:nth-child(even) {
  background: white;
}
</style>
