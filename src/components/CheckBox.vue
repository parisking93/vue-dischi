<template>
  <div>
        <input type="checkbox" id="check" name="vehicle1" @change="ordina">
        <label for="check" class="text-light text-capitalize ms-2">ordinato per data</label><br>
  </div>
</template>

<script>
import { bus } from '@/bus.js';


export default {
    name: "CheckBox",
    data() {
        return {
            ordinaLibrary : false
        }
    },
    methods : {
        ordina() {
            this.ordinaLibrary = !this.ordinaLibrary
            bus.$emit('ordinato', this.ordinaLibrary);
        }
    }

}   
</script>

<style lang="scss" scoped>
    *{
        cursor: pointer;
    }

</style>