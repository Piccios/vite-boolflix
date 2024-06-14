<script>
    export default {
        props: {
            movie: {
                type: Object,
                required: true
            }
        }
    };
</script>

<template>
    <div class="movie-item">
        <h3>{{ movie.title }}</h3>
        <p>{{ movie.original_language }}</p>
        <p>{{ movie.vote_average }}</p>
    </div>
</template>

<style scoped>
    .movie-item{
        margin-bottom: 20px;
        padding: 10px;
        border: 1px solid black;
        border-radius: 5px;
    }
</style>