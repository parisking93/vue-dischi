<template>
    <select name="scegli" v-model.trim="selectValue" @change="selectV">
        <option v-for="(genere,index) in listaAlbumGenere" :key="index" :value="genere">{{genere}}</option>
    </select>
</template>

<script>
import { bus } from '@/bus.js';
export default {
    name : 'SelectType',
    props : ['lista'],
    data() {
      return {
          selectValue : '',
          listaAlbum : [],
          listaAlbumGenere : [],
          all : 'All'
      }
    },
    watch : {
        lista :  {
            handler() {
                this.listaAlbum = this.lista

                this.listaAlbum.forEach(element => {
                    if(!this.listaAlbumGenere.includes(element.genre)) {
                        this.listaAlbumGenere.push(element.genre);
                    }
                });

            }
        }
    },
    methods : {
        selectV() {
            bus.$emit('clicked', this.selectValue);
            if(!this.listaAlbumGenere.includes(this.all)) {
                this.listaAlbumGenere.unshift(this.all)
            }   
        }
    }

}
</script>

<style>

</style>