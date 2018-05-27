<template>
  <div class="home">
    <img class="corp-logo" src="@/assets/logo.png">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
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

<style>
.corp-logo {
  width: 400px;
}

@media (max-width: 48em) {
  .corp-logo {
    width: 300px;
  }
}
</style>

