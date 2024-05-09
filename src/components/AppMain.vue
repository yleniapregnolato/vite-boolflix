<script>
import { store } from "../store";
import AppMovie from "./AppMovie.vue";
import AppTv from "./AppTv.vue";
export default {
    data() {
        return {
            store,
        };
    },
    components: { AppMovie, AppTv }
}
</script>

<template>
    <div class="container">
        <div class="row row-cols-4">
            <div class="col" v-for="movie in store.moviesArray">
                <AppMovie :movieObj="movie" />
            </div>
            <div class="col" v-for="tv in store.tvArray">
                <AppTv :tvObj="tv" />
            </div>
        </div>
    </div>
</template>