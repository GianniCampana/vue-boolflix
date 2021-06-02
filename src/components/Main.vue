<template>
  <div class="main">

      <div class="titolo1">
          <h1>FILM </h1>
      </div>

    <div class="tutti-i-film">
        <div v-for="film in films" :key="film.id" class="filmList">
            <div class="front-card">
                <img class="img-null" :src="`https://genesisairway.com/wp-content/uploads/2019/05/no-image.jpg`" :alt="film.name" v-if="film.poster_path===null">
                <img :src="`https://image.tmdb.org/t/p/w300/${film.poster_path}`" :alt="film.title" v-if="film.poster_path!==null">
            </div>
            <div class="back-card">
                <h1>Titolo: {{film.title}}</h1>
                <h1>Titolo originale: {{film.original_title}}</h1>
                <h1 v-if="bandiere.includes(film.original_language)"> <img :src="require(`../assets/img/${film.original_language}.png`)" :alt="film.original_language"> </h1>
                <h1 v-else>Lingua originale: {{film.original_language}}</h1>
                <h1 class="descrizione">Descrizione: {{film.overview}}</h1>
                <h1>Voto: <span 
                        v-for="(voto,index) in printVote(film.vote_average)" 
                        :key="index+'votoFilm'" v-html="voto">
                        </span>
                        <span v-for="(empty,index) in printeVoteEmpty(film.vote_average)" :key="index" v-html="empty" ></span>
                </h1>
            </div>
        </div> 
    </div>

        <div class="titolo2">
            <h1>SERIE TV </h1>
        </div>

    <div class="tutte-le-serie">
        <div v-for="serieTv in serie" :key="serieTv.id" class="serieList">
            <div class="front-card">
                <img class="img-null" :src="`https://genesisairway.com/wp-content/uploads/2019/05/no-image.jpg`" :alt="serieTv.name" v-if="serieTv.poster_path===null">
                <img :src="`https://image.tmdb.org/t/p/w300/${serieTv.poster_path}`" :alt="serieTv.name" v-if="serieTv.poster_path!==null">
            </div>
           <div class="back-card">
                <h1>Titolo: {{serieTv.name}}</h1>
                <h1 v-if="bandiere.includes(serieTv.original_language)"> <img :src="require(`../assets/img/${serieTv.original_language}.png`)" :alt="serieTv.original_language"></h1>
                <h1 v-else >Lingua originale: {{serieTv.original_language}}</h1>
                <h1>Voto: <span 
                       v-for="(voto, index) in printVote(serieTv.vote_average)"
                        :key="index+'votoTv'" v-html="voto">
                        </span>
                        <span v-for="(empty,index) in printeVoteEmpty(serieTv.vote_average)" :key="index" v-html="empty" ></span>
                </h1>
           </div>
        </div>
    </div>
 </div>
</template>
<script>

export default {
    name: 'Main',
    props:{
        films: Array,
        serie: Array,
       
    },
    data(){
        return{
            bandiere: ['it', 'en'],     
        }
    },
    methods:{  

        printVote(voto){
            let stars=[]
            let star= '<i class="fas fa-star"></i>'
            let votoApprossimato= Math.floor((voto)/2)
             for(let i=0; i<votoApprossimato; i++){
                stars.push(star)
            } 
            return stars
        },

        printeVoteEmpty(voto2){
            let starsEm=[]
            let starEm = '<i class="fas fa-star"></i>'
            let votoApprossimato2= Math.floor((voto2)/2)

            for(let c=0; c<votoApprossimato2; c++){
                starsEm.push(starEm)
            }
            let difference= 5-starsEm.length
            let emptyStars=[]
            let emptyStar= '<i class="far fa-star"></i>'
            for(let a=0; a<difference; a++){
                emptyStars.push(emptyStar)
            }
            return emptyStars
        }
    }  
}

</script>
<style lang='scss' scoped>

::-webkit-scrollbar {
  width: 4px;
  height: 10px;
}

::-webkit-scrollbar-track {
  border-radius: 0;
  background: #858282;
}

::-webkit-scrollbar-thumb {
  border-radius: 5px;
  background: #363636;
}
::-webkit-scrollbar-thumb:hover{
    background: #535353;
}


.main{
    width: 100%;
    min-height: 100vh;
    padding-top: 50px;
    padding-bottom: 20px;
    background-color: black;
    
    h1{
        color: rgb(255, 255, 255);
    }
    .titolo1, .titolo2{
        width: 100%;
        height: 50px;
        padding-left: 40px;
        margin-bottom: 50px;
        background-image: linear-gradient(to right, #770000 50%, #000000 100%);
        h1{
            color: black;
        }
        
    }
    .titolo2{
        margin-top: 50px;
    }
    .tutti-i-film{
        width: 100%;
        display: flex;
        overflow-y: auto;
            .back-card{
            position: absolute;
            top: 0%;
            width: 300px;
            height: 100%;
            transform: rotateY(180deg);
            background-color: rgb(27, 27, 27);
            color: white;
            padding-top: 20px;
            border: whitesmoke solid 1px;
            overflow: hidden;
            }
        
         .front-card{ 
             -webkit-backface-visibility: hidden;
             backface-visibility: hidden; 
             width: 300px;
             
             
             img{
                 width: 300px;
                 height: 500px;
             }
         }
    }
     .img-null{
                 width: 365px;
             }
    .tutte-le-serie{
       width: 100%;
       display: flex;
       overflow-y: auto;
       padding-bottom: 20px;
         .back-card{
            position: absolute;
            top: 0%;
            width: 100%;
            height: 100%;
            transform: rotateY(180deg);
            background-color: rgb(27, 27, 27);
            color: white;
            padding-top: 20px;
            border: whitesmoke solid 1px;
            
            
         }
          .front-card{ 
             -webkit-backface-visibility: hidden;
             backface-visibility: hidden; 
              width: 300px;
              
             
             img{
                 width: 300px;
                 height: 500px;
             } 
         }
       .serieList{
            position: relative;
            width: 300px;
            text-align: center;
            transition: transform 0.6s;
            transform-style: preserve-3d;
            box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
              h1{
               font-size: 20px;
               img{
                   width: 70px;
               }
           }
       }
       .serieList:hover{
           transform: rotateY(200deg);
       }
    }
    h1{
        margin-bottom: 10px;
    }
    .filmList:hover{
        transform: rotateY(200deg);
    }
    .filmList{
        margin-bottom: 20px;
        position: relative;
        width: 300px;
        text-align: center;
        transition: transform 0.6s;
        transform-style: preserve-3d;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);

        h1{
            font-size: 15px;
            img{
                width: 70px;
            }
        } 
    }
}

</style>