<template>
  <h2 class="company-title">
    {{ title}}
  </h2>
</template>

<script>
export default {
  name: 'CompanyTitle',
  props: {
    title: String
  }
}
</script>

