<template>
  <div class="flex items-center justify-center rounded-lg border-2 px-2 py-2">
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
