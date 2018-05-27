<template>
  <div class="home">
    <img class="corp-logo" src="@/assets/logo.png">
    <div class="nav">
      <router-link class="nav-link" to="/">Home</router-link>
      <router-link class="nav-link" to="/about">About</router-link>
      <router-link class="nav-link" to="/contact">Contact</router-link>
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

<style lang="scss">
.corp-logo {
  width: 500px;
}

.nav {
  margin-top: 42px;
}

.nav-link {
  color: white;
  text-decoration: none;
  font-size: 1.25em;
  font-weight: 900;
  margin-left: 15px;
  margin-right: 15px;

  &:hover {
    color: #42b983;
  }
}

@media (max-width: 48em) {
  .corp-logo {
    width: 300px;
  }
}
</style>

