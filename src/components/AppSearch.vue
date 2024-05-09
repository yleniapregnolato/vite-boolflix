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
            <input type="text" v-model="store.searchQuery">
            <button @change="$emit('filter')">CERCA</button>
        </div>
    </div>
</template>

<style scoped lang="scss"></style>