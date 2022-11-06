<template>
  <NuxtLink :to="route" class="flex items-center py-2 text-black">
    <img src="/back.svg" alt="" class="mr-4 h-[18px]" />
    <p class="text-black">Back</p>
  </NuxtLink>
</template>

<script>
export default {
  props: {
    route: {
      type: String,
      default: () => {
        return '/profile'
      },
    },
  },
}
</script>

<style lang="scss" scoped></style>
