<template>
  <h2 class="company-title">
    <a :href="url" target="_blank">{{title}}</a>
  </h2>
</template>

<script>
export default {
  name: 'CompanyTitle',
  props: {
    title: String,
    url: String
  }
}
</script>

<style scoped lang="scss">
.company-title {
  a {
    text-decoration: none;
    color: white;

    &:hover {
      color: #42b983;
    }
  }
}
</style>


