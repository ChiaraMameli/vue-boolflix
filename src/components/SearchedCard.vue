<template>
  <section>
    <h2>{{placeholder}}</h2>
    <ul v-for="item in searchedItems" :key="item.id">
        <li><img :src="item.poster" alt=""></li>
        <li>titolo: {{item.title}}</li>
        <li>titolo originale: {{item.originalTitle}}</li>
        <li>lingua: {{item.originalLanguage}}</li>
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
}
</script>

<style>

</style>