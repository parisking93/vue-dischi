<template>
    <header class="px-5 py-2 d-flex justify-content-between align-items-center">
        <div class="box-logo d-inline-block rounded-circle">
            <a href="#">
                <i class="fab fa-spotify"></i>
            </a>
        </div>
        <div class="d-flex">
            <CheckBox class="me-5"/>
            <SelectType :lista="album" />
        </div>
    </header>
</template>

<script>
import SelectType from '@/components/SelectType.vue';
import CheckBox from '@/components/CheckBox.vue';

export default {
    name : 'HeaderSpotify',
    props : ['album'],
    components : {
        SelectType,
        CheckBox
    },
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