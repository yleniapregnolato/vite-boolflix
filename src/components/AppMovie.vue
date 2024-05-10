<script>
export default {
    props: {
        movieObj: Object,
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
            // console.log('https://image.tmdb.org/t/p/' + 'w342' + poster_path);
            return ('https://image.tmdb.org/t/p/' + 'w342' + poster_path);
        },
    },
}
</script>

<template>
    <div class="ms_movie card">
        <div class="card-body"> 
            <img v-if="movieObj.poster_path !== null" :src="getPosterUrl(movieObj.poster_path)" alt=""> 
            <img class="ms_not-found" v-else src="../assets/img/not-found.png" alt="not-found">
            <h2 class="text-center"> {{ movieObj.title }} </h2>
            <h3 class="text-center"> {{ movieObj.original_title }}</h3>
            <div class="text-center d-flex justify-content-center">
                <img class="language" :src="getImageUrl(movieObj.original_language)" alt="">
                <h4 class="text-center ms-3">{{ movieObj.original_language }}</h4>
            </div>
            <h4 class="text-center">{{ movieObj.vote_average }}</h4>
            <div class="text-center"><i class="fa-regular fa-star" v-for="n in 5"></i></div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.ms_movie {
    .language {
        height: 20px;
    }

    .ms_not-found {
        height: 183px;
    }
}
</style>