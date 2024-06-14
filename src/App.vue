<script setup>
  export default{
    components:{

    }
  },
  data(){
    return{
      movies: []
    };
  },
  methods:{
    async searchMovies(query) {
      try{
        const response = await axios.get('https://api.themoviedb.org/3/search/movie'), {
          params: {
            api_key: '62e3cbd4b6904ca7307e4b3b03e03a2a',
            query: query,
            lenguage: 'it-IT'
          }
        }
      }
    }
  }
</script>

<template>
  <div id="app">

  </div>
</template>

<style scoped>

</style>
