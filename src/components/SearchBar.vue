<template>
    <div>
        <input type="text" v-model="query">
        <button @click="getItem">cerca</button>
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    data(){
        return{
            query: '',
        }
    },
    methods:{
        getItem(){
            this.$emit('search-movie', this.query)
        }
    }
}
</script>

<style>

</style>