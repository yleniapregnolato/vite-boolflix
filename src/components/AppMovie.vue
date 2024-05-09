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
        }
    }
}
</script>

<template>
    <div class="ms_movie card">
        <div class="card-body">
            <h2 class="text-center"> {{ movieObj.title }} </h2>
            <h3 class="text-center"> {{ movieObj.original_title }}</h3>
            <div class="text-center d-flex justify-content-center">
                <img :src="getImageUrl(movieObj.original_language)" alt="" >  
                <h4 class="text-center ms-3">{{ movieObj.original_language }}</h4>                        
            </div>
            <h4 class="text-center">{{ movieObj.vote_average }}</h4>
        </div>
    </div>
</template>

<style scoped lang="scss">
.ms_movie {
    img {
        height: 20px;
    }
}
</style>