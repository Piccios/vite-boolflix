<script>
// import { countries } from 'country-flag-icons';

export default {
    props: {
        item: {
            type: Object,
            required: true
        }
    },
    computed: {
        imageUrl (){
            const baseUrl = 'https://image.tmdb.org/t/p/';
            const size = 'w500';
            return `${baseUrl}${size}${this.item.poster_path}`
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
        <img :src="imageUrl" :alt="item.title || item.name">
        <p><strong>{{ item.type === 'movie' ? "Movie's Title:" : "Show's Title:" }}</strong>{{' ' + (item.title || item.name) }}</p>
        <p><strong>{{ item.type === 'movie' ? "Movie's original title:" : "Show's original name:" }}</strong>{{' ' + (item.original_title || item.original_name) }}</p>
        <p><strong>Original lenguage: </strong> <img class="flag" :src="getFlagUrl(item.original_language)" :alt="item.original_language"></p>
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

    img.flag{
        height: 20px;
        margin-left: 1.5rem;
    }

</style>