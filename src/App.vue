<template>
  <div id="app">
    <h1>Weather App</h1>
    <Weather></Weather>
  </div>
</template>

<script>
import Weather from '@/components/Weather';

export default {
  name: 'app',
  components:{
    Weather
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
