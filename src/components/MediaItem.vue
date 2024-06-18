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
            const size = 'w342';
            return `${baseUrl}${size}${this.item.poster_path}`
        }
    },
    fullStars(){
        const fullStars = Math.ceil(this.item.vote_average / 2);
        console.log('Full Stars', fullStars);
        return fullStars;
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
    }
}
</script>

<template>
        <div class="item">
            <div class="card">
                <div class="image">
                    <img :src="imageUrl" :alt="item.title || item.name">
                </div>
                
                <div class="content">
                    <p>
                        <strong>{{ item.type === 'movie' ? "Movie's Title:" : "Show's Title:" }}</strong>{{' ' + (item.title || item.name) }}
                    </p>

                    <p>
                        <strong>{{ item.type === 'movie' ? "Movie's original title:" : "Show's original name:" }}</strong>{{' ' + (item.original_title || item.original_name) }}
                    </p>

                    <p>
                        <strong>Original lenguage: </strong> <img class="flag" :src="getFlagUrl(item.original_language)" :alt="item.original_language">
                    </p>

                    <p>
                        <strong>Average review: </strong>
                    </p> 
                        <span v-for="n in 5" :key="n">
                            <i :class="n < fullStars ? 'fas fa-star' : 'far fa-star'"></i>
                        </span>
                </div>
            </div>
        </div>  
    
</template>

<style scoped>

    .item{
    position : relative;
    width : 350px;
    display : flex;
    align-items : center;
    justify-content : center;
    flex-wrap : wrap;
    padding : 30px;  
    }

    .item .card {
    position: relative;
    height : 215px;  
    background-color : #fff;
    margin : 30px 10px;
    padding : 20px 15px;
    display : flex;
    flex-direction : column;
    box-shadow : 0 5px 20px rgba(0,0,0,0.5);
    transition : 0.8s ease-in-out;
    border-radius : 15px;
    }

    div.item p strong{
        text-decoration: underline;
    }

    img.flag{
        height: 20px;
        margin-left: 1.5rem;
    }

    i.fa-star{
        color: gold;
    }

    .item .card:hover {
    height : 900px; 
    width: 400px;  
    }

    .item .card {
    position : relative;
    width : 260px;
    height : 460px;
    top : -20%;
    left: 8px;
    box-shadow : 0 5px 20px rgba(0,0,0,0.2);
    z-index : 1;
    background-color: aqua;
    }

    .item .card img {
    border-radius : 15px;
    }

    .item .card .content {
    padding : 10px 15px;
    color : #111;
    text-align : center;
    visibility : hidden;
    opacity : 0;
    transition : .3s ease-in-out;
    }

    .item .card:hover .content {
    visibility : visible;
    opacity : 1;
    transition-delay: 0.2s;
    }



</style>