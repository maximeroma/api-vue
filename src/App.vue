<template>
  <div id="app">
    <img src="./assets/logo.png">
    <starWars></starWars>
    <twitch></twitch>  
  </div>
</template>

<script>
import Hello from './components/Hello'
import StarWars from './components/StarWars'
import Twitch from './components/Twitch'

export default {
  name: 'app',
  components: {
    StarWars, 
    Twitch
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
