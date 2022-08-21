<template>

  <section>
    <h2>{{placeholder}}</h2>
    <div id="section-layout">
        <ul class="item" v-for="item in searchedItems" :key="item.id">
            <li class="poster"><img :src="item.poster" :alt="item.title"></li>
            <li>
                <div class="hover-section">
                    <ul>
                        <li>Titolo: {{item.title}}</li>
                        <li>Titolo originale: {{item.originalTitle}}</li>
                        <li>
                            <img v-if="flags.includes(item.originalLanguage)" :src="require(`../assets/img/${item.originalLanguage}.png`)" :alt="item.originalLanguage">
                            <span v-else>Lingua: {{item.originalLanguage}}</span>
                        </li>
                        <li>Voto: <span v-for="(star, i) in item.popularity" :key="i"><i class="fa-solid fa-star"></i></span></li>
                        <li>{{item.overview}}</li>
                    </ul>
                </div>
            </li>
        </ul>
    </div>
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
            flags: ['it', 'en'],
        } 
    },
    methods: {
        toNext(){
            
        }
    }
}
</script>

<style scoped lang="scss">
#section-layout {
    display: flex;
    flex-wrap: wrap;

    ul{
        list-style-type: none;
        padding: 0;
    };

    .item{
        width: 200px;
        height: 300px;
        margin: 15px;

        &:hover .hover-section{ 
            cursor: pointer;
            visibility: visible;
        }
    }
}
.poster {
    position: absolute;
    img{
        width: 200px;
        height: 300px;
    };
}

.hover-section{
    position: relative;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;

    color: white;
    background-color: rgba(0, 0, 0, 0.5);
    width: 200px;
    height: 300px;

    visibility: hidden;

    img{
        width: 30px;
    }
}

</style>