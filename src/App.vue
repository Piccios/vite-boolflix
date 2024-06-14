<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import MovieList from './components/MovieList.vue';

export default {
  components: {
    SearchBar,
    MovieList
  },
  data() {
    return {
      movies: []
    };
  },
  methods: {
    async searchMovies(query) {
      try {
        const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
          params: {
            api_key: '62e3cbd4b6904ca7307e4b3b03e03a2a',
            query: query,
            language: 'it-IT'
          }
        });
        this.movies = response.data.results;
      } catch (error) {
        console.error('Error searching movies:', error);
      }
    }
  }
};
</script>

<template>
  <div id="app">
    <SearchBar @search="searchMovies"/>
    <MovieList :movies="movies"/>
  </div>
</template>

<style scoped>

</style>
