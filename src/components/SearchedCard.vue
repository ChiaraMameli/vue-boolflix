<template>

  <section>
    <h2>{{placeholder}}</h2>
    <div id="section-layout">
        <ul class="item" v-for="item in searchedItems" :key="item.id">
            <li class="poster"><img :src="item.poster" :alt="item.title"></li>
            <li>
                <div class="hover-section">
                    <ul>
                        <li><strong>Title:</strong> {{item.title}}</li>
                        <li><strong>Original title:</strong> {{item.originalTitle}}</li>
                        <li>
                            <img v-if="flags.includes(item.originalLanguage)" :src="require(`../assets/img/${item.originalLanguage}.png`)" :alt="item.originalLanguage">
                            <span v-else><strong>Language:</strong> {{item.originalLanguage}}</span>
                        </li>
                        <li v-if="item.popularity"><strong>Rating:</strong> <span v-for="n in 5" :key="n"><i class="fa-star" :class="n >= item.popularity ? 'fa-regular' : 'fa-solid'"></i></span></li>
                        <li v-if="item.overview"><strong>Storyline:</strong> {{item.overview}}</li>
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
    }
}
</script>

<style scoped lang="scss">
h2{
    padding: 15px;
}
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

    padding: 10px;
    overflow-y: auto;

    visibility: hidden;

    img{
        width: 30px;
    }

    li{
        padding-bottom: 10px;
    }

    .fa-star{
        color: yellow;
    }
}

    ::-webkit-scrollbar {
    width: 1px;
    }


</style>