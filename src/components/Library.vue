<template>
  <div class="container px-xl-5 h-100 overflow-auto" >
        <Loader v-if="loader"/>
        <div v-else class="row justify-content-center flex-wrap pt-5 pb-4 gx-2" >
            <div v-for="(song,index) in album" :key="index" class="col-6 col-md-3 col-xl-2 m-xl-2 my-2" :data-select="index" >
                <SongCard :card="song"/>
            </div>
        </div>
  </div>
</template>

<script>
import SongCard from '@/components/SongCard.vue';
import Loader from '@/components/Loader.vue';

export default {
    name: 'Library',
    props : ["album"],
    components : {
        SongCard,
        Loader,
    },
    data() {
        return {
            loader : true,
        }
    },
    created() {
        setTimeout(()=>{
            this.loader = false;

        },600);
    }

}

</script>

<style>

</style>