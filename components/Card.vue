<template>
  <div class="flex flex-col min-h-[500px] mx-auto">
    <div>
      <h2 class="px-4 text-xl bg-[#1B2430] text-white py-6 rounded-lg fig">
        {{ heading }}
      </h2>
    </div>
    <div>
      <div class="py-6 bg-gray-50 rounded-lg my-4">
        <nuxt-img src="/phone.svg" class="h-[150px] mx-auto" />
      </div>
    </div>
    <div class="bg-[#1B2430] text-white py-8 px-4 rounded-lg">
      <h2 class="fig text-xl pb-2">Details</h2>
      <ul class="text-gray-50">
        <li class="figlight" v-for="point in points" :key="point">
          {{ point }}
        </li>
      </ul>
      <div class="max-w-[140px] mt-8">
        <Button text="learn more" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    heading: {
      type: String,
      default: () => {
        return ''
      },
    },
    points: {
      type: Array,
      default: () => {
        return []
      },
    },
  },
}
</script>

<style scoped>
li {
  margin-bottom: 0.4rem;
}
</style>
