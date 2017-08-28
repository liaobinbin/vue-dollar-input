<template>
  <div id="app">
    <img src="./assets/logo.png">
    <money-input></money-input>
  </div>
</template>

<script>
import MoneyInput from './components/MoneyInput'

export default {
  name: 'app',
  components: {
    MoneyInput
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
