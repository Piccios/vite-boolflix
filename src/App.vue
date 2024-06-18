<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import MediaList from './components/MediaList.vue';

export default {
  components: {
    SearchBar,
    MediaList
  },
  data() {
    return {
      items: []
    };
  },
  methods: {
    async searchMedia(query) {
      try {
        const apiKey = '62e3cbd4b6904ca7307e4b3b03e03a2a';
        const [movieResponse, tvResponse] = await Promise.all([
          axios.get('https://api.themoviedb.org/3/search/movie', {
            params: {
              api_key: apiKey,
              query: query,
              language: 'it-IT'
            }
          }),
          axios.get('https://api.themoviedb.org/3/search/tv', {
            params: {
              api_key: apiKey,
              query: query,
              language: 'it-IT'
            }
          })
        ]);

        const movies = movieResponse.data.results.map(item => ({
          ...item,
          type: 'movie'
        }));
        const tvShows = tvResponse.data.results.map(item => ({
          ...item,
          type: 'tv'
        }));

        this.items = [...movies, ...tvShows];
      } catch (error) {
        console.error('Error searching media:', error);
      }
    }
  }
};
</script>

<template>
  <header>
    <div class="logo">
      <img class="logo" src="../src/assets/logo.png" alt="PiccioFlix_logo">
      <h1>PiccioFlix</h1>
    </div>
    <SearchBar @search="searchMedia"/>
  </header>
  <main>
    <div id="app">
    
    <MediaList :items="items"/>
  </div>
</main>
  
</template>

<style scoped>
  header{
    display: flex;
    justify-content: space-around;
    margin: 1.5rem .5rem; 
    align-items: center;
    color: rgb(16, 63, 106);
  }

  main{
    display: flex;
    justify-content: space-between;
    margin: 0 2.5rem;
  }

  div.logo{
    display: flex;
    align-items: center;
  }

  img.logo{
    height: 150px;
  }
</style>
