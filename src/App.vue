<template>
  <div id="app">
    <HeaderSpotify/>
    <main class="position-relative">
      <Library />
    </main>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import HeaderSpotify from './components/HeaderSpotify.vue'
import Library from './components/Library.vue'



export default {
  name: 'App',
  components: {
    HeaderSpotify,
    Library
    // HelloWorld
  }
}
</script>

<style lang="scss">
  @import '@/style/general.scss';


  #app {
    main {
      height: calc(100vh - 61px);
      background-color: #1e2d3b;
    }

  }
</style>
