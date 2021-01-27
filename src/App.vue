<template>
  <div id="app">
  <UserFetch/> 
  </div>
</template>

<script>
import UserFetch from './components/UserFetch.vue';

export default {
  name: 'App',
  components: {
    UserFetch
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>