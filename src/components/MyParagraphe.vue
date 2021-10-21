<template>
    <p>{{ text }}</p>
    <p class="my-paragraphe" :class="classes">
      {{ text }}
    </p>
</template>

<script>
import { computed } from 'vue'
export default {
  props: {
    text: {
      type: String,
      required: true
    },
    color: {
      type: String,
      default: 'black'
    }
  },
  setup (props) {
    const classes = computed(() => {
      return `my-paragraphe--${props.color}`
    })

    return {
      classes
    }
  }
}
</script>

<style lang="scss" scoped>
    .my-paragraphe {
      color: black;

      &--red{
        color: red;
      }
      &--blue{
        color: blue;
      }
      &--green{
        color: green;
      }
    }
</style>
