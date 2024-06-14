<script>
import MovieItem from './MovieItem.vue'

export default {
    components: {
        MovieItem
    },
    props: {
        movies: {
            type: Array,
            required: true,
            default:() => []
        }
    }
};

</script>
<template>
    <div v-for="movie in movies" :key="movie.id">
        {{ console.log(movie) }}
        <MovieItem :movie="movie" />
    </div>
</template>
<style></style>