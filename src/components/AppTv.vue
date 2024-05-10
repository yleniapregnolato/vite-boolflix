<script>
export default {
    props: {
        tvObj: Object
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
            let voteRound = Math.ceil(this.tvObj.vote_average / 2) ; 
            return voteRound;

        },
    },
}
</script>

<template>
    <div class="ms_tv card">
        <div class="card-body">
            <div class="text-center"><img :src="getPosterUrl(tvObj.poster_path)" alt=""></div>
            <h2 class="text-center"> {{ tvObj.name }} </h2>
            <h3 class="text-center"> {{ tvObj.original_name }}</h3>
            <div class="text-center d-flex justify-content-center">
                <img class="language" :src="getImageUrl(tvObj.original_language)" alt="" >  
                <h4 class="text-center ms-3">{{ tvObj.original_language }}</h4>                        
            </div>
            <h4 class="text-center">{{ getVote(tvObj.vote_average) }}</h4>
            <div class="text-center"><i class="fa-regular fa-star" v-for="n in 5"></i></div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.ms_tv {
    .language {
        height: 20px;
    }
}
</style>