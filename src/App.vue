<template>
  <div id="app">   
    <h1>Página</h1>     
    <cliente/>
    <cliente/>
    <cliente/>
    <cliente/>
  </div>
</template>

<script>
import cliente from './components/cliente.vue'

export default {
  name: 'App',
  components: {
    cliente
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
