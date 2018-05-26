<template>
  <div class="home">
    <img src="../assets/logo.png">
    <Companies />
  </div>
</template>

<script>
import Companies from '@/components/Companies';

export default {
  name: 'Home',
  components: {
    Companies
  },
}
</script>
