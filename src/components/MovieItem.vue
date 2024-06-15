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
        <p><strong>Movie's Title:</strong>{{' ' + movie.title }}</p>
        <p><strong>Movie's original title: </strong>{{' ' + movie.original_title }}</p>
        <p><strong>Original lenguage: </strong>{{' ' + movie.original_language }}</p>
        <p><strong>Average review: </strong>{{' ' + movie.vote_average }}</p>
    </div>
</template>

<style scoped>
    .movie-item{
        margin-bottom: 20px;
        padding: 10px;
        border: 1px solid black;
        border-radius: 5px;
    }

    div.movie-item p strong{
        text-decoration: underline;
    }
</style>