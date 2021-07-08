<template>
    <header class="px-5 py-2">
        <div class="box-logo d-inline-block rounded-circle">
            <a href="#">
                <i class="fab fa-spotify"></i>
            </a>
        </div>
    </header>
</template>

<script>
export default {
    name : 'HeaderSpotify'
}
</script>
<style lang="scss" scoped>
    header {
        background: #2e3a46;

        .box-logo {
            background: black;

            i {
                color: #1dd760;
                font-size: 45px;
            }
    }
    }


</style>