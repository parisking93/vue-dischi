<template>
  <div id="app">
    <HeaderSpotify :album="libraryListPass" />
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
      libraryListPass : "",
      genereSelezionato : 'All',
      ordinaLibri : false
    }
  },
  mounted(){
      this.getLibrary();
      setTimeout(()=>{
        this.libraryListPass = this.libraryList;  

      },800)
      bus.$on('selected', (selectGenere)=>{

        this.genereSelezionato = selectGenere;
        this.filtraGenere(selectGenere);

        if(this.ordinaLibri) {
          this.libraryListPass.sort(this.comparaArrObj);
          
        }

      });

      bus.$on('ordinato',(ordinaLibrary)=>{
        this.ordinaLibri = ordinaLibrary;
        if(ordinaLibrary) {
          this.libraryListPass.sort(this.comparaArrObj);
          this.getLibrary()
        } else {
          this.libraryListPass = this.libraryList;
          if(this.genereSelezionato !='All') {
            this.filtraGenere(this.genereSelezionato);
          } 

        }
      });    
  },
  methods: {

      getLibrary(){
          axios
              .get(this.apiLink)
              .then(response => {
                  this.libraryList = response.data.response;
                  // this.libraryListPass = this.libraryList;

              })
              .catch(error => {
                  console.log('Errore: ', error);
              });
          
      },
      comparaArrObj(element1, element2) {
        if (element1.year > element2.year) return 1;
        if (element2.year > element1.year) return -1;

        return 0;
      },
      filtraGenere(genere) {
          if(genere != 'All') {

            this.libraryListPass = this.libraryList.filter(element=> {
              if(element.genre == genere) {
                return element.genre
              }
            });
        } else {
          this.libraryListPass = this.libraryList;
        }
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
