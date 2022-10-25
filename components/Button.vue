<template>
  <div
    class="flex items-center justify-center rounded-lg border-2 px-2 py-2 ripple"
  >
    <p class="figlight">{{ text }}</p>
  </div>
</template>

<script>
export default {
  props: {
    text: String,
    default: () => {
      return ''
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
</style>
