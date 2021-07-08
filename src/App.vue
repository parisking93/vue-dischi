<template>
  <div id="app">
    <HeaderSpotify/>
    
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import HeaderSpotify from './components/HeaderSpotify.vue'


export default {
  name: 'App',
  components: {
    HeaderSpotify
    // HelloWorld
  }
}
</script>

<style lang="scss">
  @import '@/style/general.scss';


  #app {


  }
</style>
