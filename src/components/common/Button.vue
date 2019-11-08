<template>
  <button :class="classes" @click="$emit('click', $event)">
    <slot />
  </button>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      default: 'teal'
    }
  },
  computed: {
    classes () {
      const { color } = this
      return [`bg-${color}-500 hover:bg-${color}-600 text-white font-bold py-2 px-4 rounded-lg uppercase text-sm`]
    }
  }
}
</script>
