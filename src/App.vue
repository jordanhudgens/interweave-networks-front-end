<template>
  <div id="app">
    <Home />
  </div>
</template>

<script>
import Home from '@/components/Home';

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>


<style lang="scss">
#app {
  position: absolute;
  top: 0;
  left: 0;
  padding-top: 42px;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  background-color: #29394b;
}
</style>
