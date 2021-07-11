<template>
  <div id="app">
    <HeaderSpotify :album="libraryList"/>
    <main>
      <Library :album="libraryListPass"/>
    </main>
  </div>
</template>

<script>
import HeaderSpotify from './components/HeaderSpotify.vue';
import Library from './components/Library.vue';
import axios from 'axios';
import { bus } from '@/bus.js';
import dayjs from 'dayjs';

console.log(dayjs().format('hh'));
var minMax = require('dayjs/plugin/minMax')
dayjs.extend(minMax)

export default {
  name: 'App',
  components: {
    HeaderSpotify,
    Library
  },
  data(){
    return {
      libraryList : [],
      apiLink :  'https://flynn.boolean.careers/exercises/api/array/music',
      libraryListPass : ""

    }
  },
  created(){
      this.getLibrary();
      bus.$on('clicked', (selectGenere)=>{
        if(selectGenere != 'All') {
          this.libraryListPass = this.libraryList.filter(element=> {
            if(element.genre == selectGenere) {
              return element.genre

            }
          });
        } else {
          this.libraryListPass = this.libraryList;
        }
      });    
  },
  methods: {

      getLibrary(){
          axios
              .get(this.apiLink)
              .then(response => {
                  this.libraryList = response.data.response;
                  this.libraryListPass = this.libraryList;
                  this.libraryListPass.sort(this.comparaArrObj)
                  setTimeout(()=>{
                      this.loader = false;
                  },600);
              })
              .catch(error => {
                  console.log('Errore: ', error);
              });
      },
      comparaArrObj(element1, element2) {
        if (element1.year > element2.year) return 1;
        if (element2.year > element1.year) return -1;

        return 0;
      }
  
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
