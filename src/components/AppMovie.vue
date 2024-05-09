<script>
export default {
    props: {
        movieObj: Object,
    },
}
</script>

<template>
    <div class="ms_movie">
        <h2> {{ movieObj.title }} </h2>
        <h3> {{ movieObj.original_title }}</h3>
        <h4>{{ movieObj.original_language }}</h4>
        <h4>{{ movieObj.vote_average }}</h4>
    </div>
</template>