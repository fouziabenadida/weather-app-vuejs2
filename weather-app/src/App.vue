<template>
  <div id="app">
  <meteo-app></meteo-app>
  </div>
</template>

<script>
import Meteo from './components/Meteo.vue'

export default {
  name: 'App',
  components: {
   'meteo-app': Meteo
  }
}
</script>

<style >
body{
  background: #a8ff78;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right, #78ffd6, #a8ff78);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right, #78ffd6, #a8ff78); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

}
</style>>





