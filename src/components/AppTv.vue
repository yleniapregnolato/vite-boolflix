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
                <img :src="getImageUrl(tvObj.original_language)" alt="" >  
                <h4 class="text-center ms-3">{{ tvObj.original_language }}</h4>                        
            </div>
            <h4 class="text-center">{{ tvObj.vote_average }}</h4>
        </div>
    </div>
</template>

<style scoped lang="scss">
.ms_tv {
    img {
        height: 20px;
    }
}
</style>