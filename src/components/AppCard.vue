<script>
export default {
    props: {
        cardObj: Object
    },
    data() {
        return {

        }
    },
    methods: {
        getImageUrl(name) {
            return new URL('../assets/img/' + name + '.png', import.meta.url).href;
        },

        getPosterUrl(poster_path) {
            return new URL('https://image.tmdb.org/t/p/' + 'w342' + poster_path, import.meta.url).href;
        },


        getVote() {
            let voteResult = parseInt(this.cardObj.vote_average.toFixed() / 2);
            return voteResult;

        },
    }
}
</script>

<template>
    <div class="card">
        <div class="card-body">
            <img v-if="cardObj.poster_path !== null" :src="getPosterUrl(cardObj.poster_path)" alt="">
            <img class="ms_not-found" v-else src="../assets/img/not-found.png" alt="not-found">
            <h2 v-if="cardObj.title">{{ cardObj.title }} hell</h2>
            <h2 class="text-center" v-else> {{ cardObj.name }} </h2>
            <h3 class="text-center"> {{ cardObj.original_name }}</h3>
            <div class="text-center d-flex justify-content-center">
                <img class="language" :src="getImageUrl(cardObj.original_language)" alt="">
                <h4 class="text-center ms-3">{{ cardObj.original_language }}</h4>
            </div>
            <div class="text-center">
                <i class="fa-solid fa-star" v-for="n in getVote()"></i>
                <i class="fa-regular fa-star" v-for="n in 5 - getVote()"></i>
            </div>
        </div>

    </div>
</template>

<style scoped lang="scss">
.card {
    .language {
        height: 20px;
    }

    .ms_not-found {
        max-width: 100%;
        height: 183px;
        object-fit: cover;
    }
}
</style>