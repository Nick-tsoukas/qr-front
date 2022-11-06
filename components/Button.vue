<template>
  <div
    class="flex items-center justify-center rounded-lg border-2 border-[#9b71fc] px-2 py-2 ripple"
  >
    <p class="figlight">{{ text }}</p>
  </div>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      default: () => {
        return ''
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
  background: #9b71fc radial-gradient(circle, transparent 1%, #8557f1 1%)
    center/15000%;
}
.ripple:active {
  background-color: #9b71fc;
  background-size: 100%;
  transition: background 0s;
}
</style>
