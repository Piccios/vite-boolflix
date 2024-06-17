<script>
import { countries } from 'country-flag-icons';

export default {
    props: {
        movie: {
            type: Object,
            required: true
        }
    },
    methods: {
        getFlagUrl(language) {
            const languageToCountryMap = {
                'en': 'gb',
                'it': 'it',
                'fr': 'fr',
                'de': 'de',
                'es': 'es',
                'ja': 'jp',
                'ko': 'kr',
                'zh': 'cn'
            };
            const countryCode = languageToCountryMap[language] || 'un';
            return `https://cdnjs.cloudflare.com/ajax/libs/flag-icon-css/3.4.6/flags/4x3/${countryCode}.svg`;
        }
    }}
</script>

<template>
    <div class="movie-item">
        <p><strong>Movie's Title:</strong>{{' ' + movie.title }}</p>
        <p><strong>Movie's original title: </strong>{{' ' + movie.original_title }}</p>
        <p><strong>Original lenguage: </strong> <img :src="getFlagUrl(movie.original_language)" :alt="movie.original_language"></p>
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

    img {
        height: 20px;
        margin-left: 1.5rem;
    }
</style>