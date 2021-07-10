<template>
        <div class="s-card w-100 text-center p-3 h-100 m-0 " >
                <img class="w-100" :src="card.poster" alt="card.author">
                <h6 class="text-uppercase text-light my-2 ">{{card.title}}</h6>
                <div class="text-secondary">{{card.author}}</div>
                <span class="text-secondary">{{card.year}}</span>
        </div>
</template>

<script>
export default {
    name:'SongCard',
    props : ["card"],

}
</script>

<style>
    .s-card {
        background-color: rgba(255,255,255,0.1);
    }
</style>