<template>
    <header class="px-5 py-2 d-flex justify-content-between align-items-center">
        <div class="box-logo d-inline-block rounded-circle">
            <a href="#">
                <i class="fab fa-spotify"></i>
            </a>
        </div>
        <div>
            <SelectType/>
        </div>
    </header>
</template>

<script>
import SelectType from '@/components/SelectType.vue';
export default {
    name : 'HeaderSpotify',
    components : {
        SelectType
    }
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