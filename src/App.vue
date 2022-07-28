<template>
<div>
  <SearchBar @search-movie="getData"/>
  <div id="sections">
    <section v-if="searchedMovies.length > 0">
      <h2>MOVIES:</h2>
      <ul v-for="movie in searchedMovies" :key="movie.id">
        <li>titolo: {{movie.title}}</li>
        <li>titolo originale: {{movie.originalTitle}}</li>
        <li>lingua: {{movie.originalLanguage}}</li>
        <li>popolarità {{movie.popularity}}</li>
      </ul>
    </section>

    <section v-if="searchedTvSeries.length > 0">
      <h2>TV SERIES:</h2>
      <ul v-for="serie in searchedTvSeries" :key="serie.id">
        <li>titolo: {{serie.title}}</li>
        <li>titolo originale: {{serie.originalTitle}}</li>
        <li>lingua: {{serie.originalLanguage}}</li>
        <li>popolarità; {{serie.popularity}}</li>
      </ul>
    </section>
  </div>
</div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar.vue';

export default {
  name: 'App',
  components: {
    SearchBar
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
          const title = movie.title
          const originalTitle = movie.original_title
          const originalLanguage = movie.original_language
          const id = movie.id
          const popularity = movie.popularity
          movie = {title, originalTitle, originalLanguage, popularity, id}
          this.searchedMovies.push(movie)
        })})},

    getSeries(){
      this.searchedTvSeries = [];
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=2acda1a8a6a5a953521ce22c6319420c&query=${this.query}`).then((res) => {
        const series = res.data.results;
        console.log(series)
        series.forEach(serie => {
          const title = serie.name
          const originalTitle = serie.original_name
          const originalLanguage = serie.original_language
          const id = serie.id
          const popularity = serie.popularity
          serie = {title, originalTitle, originalLanguage, popularity, id}
          this.searchedTvSeries.push(serie)
      })})}
    
  }
}
</script>

<style lang="scss">
#sections{
  display: flex;
  justify-content:space-between;
}
</style> =
