<template>
  <div
    class="flex items-center justify-center rounded-lg border-2 px-2 py-2 ripple shadow-md overflow-scroll w-1/2"
    :class="typeClass"
  >
    <nuxt-img v-if="icon" :src="icon" width="30" height="30" />
  </div>
</template>

<script>
export default {
  props: {
    icon: {
      type: String,
      default: () => {
        return null
      },
    },
    typeClass: {
      type: String,
      default: () => {
        return 'facebook'
      },
    },
  },
}
</script>

<style scoped>
.ripple {
  background-position: center;
  transition: background 0.8s;
}
.ripple:hover {
  background: #47a7f5 radial-gradient(circle, transparent 1%, #47a7f5 1%)
    center/15000%;
}
.ripple:active {
  background-color: #6eb9f7;
  background-size: 100%;
  transition: background 0s;
}
.facebook {
  background: #3b5997;
}
.spotify {
  background: black;
}
</style>
