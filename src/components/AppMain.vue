<script>
import { store } from "../store";
import AppCard from "./AppCard.vue";
export default {
    data() {
        return {
            store,
        };
    },
    components: { AppCard }
}
</script>

<template>
    <div class="container">
        <div class="row row-cols-4">
            <div class="col" v-for="movie in store.moviesArray">
                <AppCard :cardObj="movie" />
            </div>

            <div class="col" v-for="tv in store.tvArray">
                <AppCard :cardObj="tv" />
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">

</style>