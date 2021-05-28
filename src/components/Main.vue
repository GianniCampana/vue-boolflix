<template>
  <div class="main">

        <div class="tutti-i-film">

            <h1>FILM TROVATI:</h1>

            <div v-for="(film,index) in films" :key="index" class="filmList">  
                <img :src="`https://image.tmdb.org/t/p/w300/${film.poster_path}`" :alt="film.title">
                <h1>Titolo: {{film.title}}</h1>
                <h1>Titolo originale: {{film.original_title}}</h1>
                <h1 v-if="bandiere.includes(film.original_language)"> <img :src="require(`../assets/img/${film.original_language}.png`)" :alt="film.original_language"> </h1>
                <h1 v-else>Lingua originale: {{film.original_language}}</h1>
                <h1>Voto: {{film.vote_average}}</h1>
            </div>
   
        </div>


    <div class="tutte-le-serie">

        <h1>SERIE TV TROVATE:</h1>

        <div v-for="(serieTv, index) in serie" :key="index" class="serieList">
            <img :src="`https://image.tmdb.org/t/p/w300/${serieTv.poster_path}`" :alt="serieTv.name">
            <h1>Titolo: {{serieTv.name}}</h1>
            <h1 v-if="bandiere.includes(serieTv.original_language)"> <img :src="require(`../assets/img/${serieTv.original_language}.png`)" :alt="serieTv.original_language"></h1>
            <h1 v-else >Lingua originale: {{serieTv.original_language}}</h1>
            <h1>Voto: {{serieTv.vote_average}}</h1>
        </div>

    </div>
 </div>
</template>

<script>
export default {
    name: 'Main',

    props:{
        films: Array,
        serie: Array
    },

    data(){
        return{
            bandiere: ['it', 'en']
        }
    },

    methods:{
    }
    
}
</script>

<style lang='scss' scoped>

.main{
    width: 100%;
     min-height: 100vh;
    background-color: gray;
    display: flex;
    .tutti-i-film{
        
        width: 50%;
        
    }
    .tutte-le-serie{
       width: 50%;
       .serieList{
           h1{
               img{
                   width: 70px;
               }
           }
       }
       
    }
    h1{
        margin-bottom: 30px;
    }
    .filmList{
        margin-bottom: 100px;
        h1{
            img{
                width: 70px;
            }
        }
        
    }
}

</style>