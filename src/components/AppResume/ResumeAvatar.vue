<template>
  <div class="avatar">
    <img :src="value">
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      validator(v) {
        const isMinLength = v.length > 3
        const isImageType = (/\.(gif|jpg|jpeg|tiff|png)$/i).test(v)
        return isMinLength && isImageType
      }
    },
  }
}
</script>

<style>

</style>