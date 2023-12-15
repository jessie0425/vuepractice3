<template>
  <div id="app">
    <EmployView></EmployView>
  </div>
</template>

<script>
import EmployView from './components/EmployView.vue'

export default {
  name: 'App',
  components: {
    EmployView
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
