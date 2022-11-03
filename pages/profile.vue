<template>
  <div>
    <pre>{{ qrs }}</pre>
    <section class="rounded-sm">
      <!-- Header of qr list -->
      <div class="flex bg-black text-white px-2 py-4">
        <p class="w-[40%]">Name</p>
        <div class="flex justify-end w-[60%]">
          <p class="w-[20%]">Link</p>
          <p class="w-[20%]">View</p>
          <p class="w-[20%]">Edit</p>
        </div>
        <hr />
      </div>
      <div class="flex px-2 py-4 striped">
        <p class="w-[40%]">Some Name</p>
        <div class="flex justify-end items-center w-[60%]">
          <div class="w-[20%]">
            <img class="w-[30px]" src="/linkicon.svg" />
          </div>
          <div class="w-[20%]">
            <img class="w-[25px]" src="/viewicon.svg" />
          </div>
          <div class="w-[20%]">
            <img class="w-[25px]" src="/editicon.svg" />
          </div>
        </div>
      </div>
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
