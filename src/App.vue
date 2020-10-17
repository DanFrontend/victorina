<template>
  <div id="app">
    <Films />
  </div>
</template>

<script>

import Films from './views/Films'
export default {
  name: 'App',
  components: {
    Films,
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
