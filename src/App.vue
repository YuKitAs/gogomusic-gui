<template>
  <div id="app">
    <h2>Go Electro Ear</h2>
    <home/>
  </div>
</template>

<script>
import Home from '@/components/Home'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style>
body {
  background-color: #12b886;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
