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
    <div class="item">
        <p><strong>{{ item.type === 'movie' ? "Movie's Title:" : "Show's Title:" }}</strong>{{' ' + (item.title || item.name) }}</p>
        <p><strong>{{ item.type === 'movie' ? "Movie's original title:" : "Show's original name:" }}</strong>{{' ' + (item.original_title || item.original_name) }}</p>
        <p><strong>Original lenguage: </strong> <img :src="getFlagUrl(item.original_language)" :alt="item.original_language"></p>
        <p><strong>Average review: </strong>{{' ' + item.vote_average }}</p>
    </div>
</template>

<style scoped>
    .item{
        margin-bottom: 20px;
        padding: 10px;
        border: 1px solid black;
        border-radius: 5px;
    }

    div.item p strong{
        text-decoration: underline;
    }

    img {
        height: 20px;
        margin-left: 1.5rem;
    }
</style>