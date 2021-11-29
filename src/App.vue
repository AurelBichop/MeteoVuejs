<template>
  <meteo></meteo>
</template>

<script>
import Meteo from './components/Meteo.vue'

export default {
  name: 'App',
  components: {
    meteo : Meteo
  }
}
</script>

<style>
  body{
    background: #43c6ac;
    background: linear-gradient(to right, #09eebc, #666517);
    
  }
</style>
