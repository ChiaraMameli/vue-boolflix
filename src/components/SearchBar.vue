<template>
    <header>
        <div>
            <img src="../assets/img/logo.png" alt="">
        </div>
        <div>
            <label class="search" for="search-item">
                <input id="search-item" type="text" v-model="query" @keyup.enter="getItem">
            </label>
        </div>
    </header>
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

<style scoped lang="scss">
header{
    display: flex;
    justify-content: space-between;
    padding: 10px;
    background-image: linear-gradient(rgba(0,0,0,1), rgba(0,0,0,0));

    img{
        height: 30px;
        cursor: pointer;
    }
}


</style>