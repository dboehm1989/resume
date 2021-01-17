<template>
  <h1>{{ value }}</h1>
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