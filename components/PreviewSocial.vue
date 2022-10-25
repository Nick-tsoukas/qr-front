<template>
  <div></div>
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
        return ''
      },
    },
  },
}
</script>

<style lang="scss" scoped></style>
