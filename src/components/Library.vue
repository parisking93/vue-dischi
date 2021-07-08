<template>
  <div class="container px-xl-5 h-100 overflow-auto">
      <div class="row justify-content-center flex-wrap h-100 py-4 gx-2">
          <div v-for="(song,index) in libraryList" :key="index" class="col-6 col-md-3 col-xl-2 m-xl-2 my-2">
            <SongCard :card="song" />
          </div>
      </div>
  </div>
</template>

<script>
// import 'axios';
import axios from 'axios';
import SongCard from '@/components/SongCard.vue';

export default {
    name: 'Library',
    components : {
        SongCard
    },
    data() {
        return {
            apiLink :  'https://flynn.boolean.careers/exercises/api/array/music',
            libraryList : []

        }
    },
    created(){
        this.getLibrary();
    },
    methods: {
        getLibrary(){
            axios
                .get(this.apiLink)
                .then(response => {
                    this.libraryList = response.data.response;
                    console.log(response.data.response);
                })
                .catch(error => {
                    console.log('Errore: ', error);
                });
        }
    }
}

</script>

<style>

</style>