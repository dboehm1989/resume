<template>
  <h2>{{ value }}</h2>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      validator(v) {
        const isMinLength = v.length > 3
        return isMinLength
      }
    },
  }
}
</script>

<style>

</style>