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
            <div class="ms_img">
                <img v-if="cardObj.poster_path !== null" :src="getPosterUrl(cardObj.poster_path)" alt="">
                <img class="ms_not-found" v-else src="../assets/img/not-found.png" alt="not-found">
            </div>
            <div class="ms_info">
                <h4 v-if="cardObj.title">Titolo: {{ cardObj.title }}</h4>
                <p class="text-center" v-else>Titolo: {{ cardObj.name }}</p>
                <p class="text-center" v-if="cardObj.original_title">TItolo originale: {{ cardObj.original_title }}</p>
                <p class="text-center" v-else>TItolo originale: {{ cardObj.original_name }}</p>
                <div class="text-center d-flex justify-content-center">
                    <img class="language" :src="getImageUrl(cardObj.original_language)" alt="">
                    <p class="text-center ms-3">Lingua: {{ cardObj.original_language }}</p>
                </div>
                <div class="text-center">                  
                    <i class="fa-solid fa-star" v-for="n in getVote()"></i>
                    <i class="fa-regular fa-star" v-for="n in 5 - getVote()"></i>
                </div>
            </div>

        </div>

    </div>
</template>

<style scoped lang="scss">
.card {
    &:hover {
        .ms_info {
            display: block;
        }

        .ms_img {
            display: none;
        }
    }

    .ms_info {
        display: none;
        text-align: start;
    }

    .language {
        height: 20px;
    }

    .ms_not-found {
        max-width: 100%;
        height: 183px;
        object-fit: cover;
    }
}</style>