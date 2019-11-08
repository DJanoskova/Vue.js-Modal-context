<template>
  <div :class="classes">
    <span class="block sm:inline">{{ text }}</span>
  </div>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      value: 'error' | 'info' | 'success' | 'warning'
    },
    text: String
  },
  computed: {
    color () {
      switch (this.type) {
        case 'error':
          return 'red'
        case 'success':
          return 'teal'
        case 'warning':
          return 'orange'
        case 'info':
        default:
          return 'gray'
      }
    },
    classes () {
      const { color } = this
      return [`bg-${color}-400 border border-${color}-200 text-white px-4 py-3 rounded-lg relative`]
    }
  },
}
</script>
