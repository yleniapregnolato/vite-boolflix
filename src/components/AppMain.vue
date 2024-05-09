<script>
import { store } from "../store";
import AppMovie from "./AppMovie.vue";
export default {
    data() {
        return {
            store,
        };
    },
    components: { AppMovie }
}
</script>

<template>
    <div class="container">
        <div class="row row-cols-4">
            <div class="col" v-for="movie in store.moviesArray">
                <AppMovie :movieObj="movie" />
            </div>
        </div>
    </div>
</template>