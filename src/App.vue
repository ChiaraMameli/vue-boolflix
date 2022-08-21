<template>
<div>
  <SearchBar @search-movie="getData"/>
  <SearchedCard placeholder="Movies:" :searchedItems="searchedMovies" v-if="searchedMovies.length > 0"/>
  <SearchedCard placeholder="TV Series:" :searchedItems="searchedTvSeries" v-if="searchedTvSeries.length > 0"/>
</div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar.vue';
import SearchedCard from './components/SearchedCard.vue';

export default {
  name: 'App',
  components: {
    SearchBar,
    SearchedCard,
},
 data(){
      return {
        query: '',
        searchedMovies: [],
        searchedTvSeries: [],

        }
  },
  methods:{
    getData(query){
      this.query = query

      this.getMovies()
      this.getSeries()
    },

    getMovies(){
      this.searchedMovies = [];
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=2acda1a8a6a5a953521ce22c6319420c&query=${this.query}`).then((res) => {
        const movies = res.data.results;
        movies.forEach(movie => {
          const poster = `https://image.tmdb.org/t/p/w185${movie.poster_path}`
          const title = movie.title
          const originalTitle = movie.original_title
          const originalLanguage = movie.original_language
          const id = movie.id
          const popularity = Math.ceil(movie.vote_average / 2)
          movie = {poster, title, originalTitle, originalLanguage, popularity, id}
          this.searchedMovies.push(movie)
        })})},

    getSeries(){
      this.searchedTvSeries = [];
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=2acda1a8a6a5a953521ce22c6319420c&query=${this.query}`).then((res) => {
        const series = res.data.results;
        console.log(series)
        series.forEach(serie => {
          const poster = `https://image.tmdb.org/t/p/w185${serie.poster_path}`
          const title = serie.name
          const originalTitle = serie.original_name
          const originalLanguage = serie.original_language
          const id = serie.id
          const popularity = Math.ceil(serie.vote_average / 2)
          serie = {poster, title, originalTitle, originalLanguage, popularity, id}
          this.searchedTvSeries.push(serie)
      })})}
    
  }
}
</script>

<style lang="scss">
*{
  box-sizing: border-box;
  margin: 0;
  border: 0;
};

body {
  background-color: #141414;
  color: #fff;
}

</style> =
