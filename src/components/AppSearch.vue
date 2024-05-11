<script>
import { store } from "../store";
export default {
    data() {
        return {
            store,
        };
    },

}
</script>

<template>
    <div class="container-fluid d-flex justify-content-between">
        <div class="ms_title">
            <h1>BOOLFLIX</h1>
        </div>
        <div class="ms_search">
            <input type="text" aria-label="inizia la ricerca" v-model="store.searchQuery">
            <button @click="$emit('search')">CERCA</button>
        </div>
    </div>
</template>

<style scoped lang="scss">
h1 {
    color: red;
}
</style>