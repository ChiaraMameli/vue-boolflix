<template>
  <section>
    <h2>{{placeholder}}</h2>
    <ul v-for="item in searchedItems" :key="item.id">
        <li><img :src="item.poster" alt=""></li>
        <li>{{item.title}}</li>
        <li>{{item.originalTitle}}</li>
        <li>
            <img v-if="flags.includes(item.originalLanguage)" :src="require(`../assets/img/${item.originalLanguage}.png`)" :alt="item.originalLanguage">
            <span v-else>{{item.originalLanguage}}</span>
        </li>
            
        <li><span v-for="(star, i) in item.popularity" :key="i"><i class="fa-solid fa-star"></i></span></li>
    </ul>

  </section>
</template>

<script>
export default {
    name: 'SearchedCard',
    props:{
        searchedItems: Array,
        placeholder: String,
    },
    data(){
        return{
            flags: ['it', 'en']
        } 
    }
}
</script>

<style>

</style>