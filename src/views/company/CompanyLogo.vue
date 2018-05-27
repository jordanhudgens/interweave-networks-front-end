<template>
  <div>
    <img class="homepage-logo" :src="logo">
  </div>
</template>

<script>
export default {
  props: {
    logo: String
  }
}
</script>

<style scoped>
.homepage-logo {
  width: 300px;
}
</style>

