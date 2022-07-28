<template>
  <div>
    <input type="text" v-model="query">
    <button @click="getMovies">cerca</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  components: {
  },
  data(){
    return{
      query: '',
    }
  },
  methods:{

    getMovies(){
    axios.get(`https://api.themoviedb.org/3/search/movie?api_key=2acda1a8a6a5a953521ce22c6319420c&query=${this.query}`).then((res) => {
      console.log(res.data.results)
    })}
  }
}
</script>

<style lang="scss">
</style>
