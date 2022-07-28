<template>
  <SearchBar @search-movie="getData"/>
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
        query: ''}
  },
  methods:{
    getData(query){
      this.query = query

      this.getMovies()
    },

    getMovies(){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=2acda1a8a6a5a953521ce22c6319420c&query=${this.query}`).then((res) => {
      console.log(res.data.results)
    })}
  }
}
</script>

<style lang="scss">
</style>
