<template>
  <div class="main">

 <div class="tutti-i-film">
       <h1>FILM TROVATI:</h1>
   <div v-for="(film,index) in films" :key="index" class="filmList">

           <h1>Titolo: {{film.title}}</h1>
           <h1>Titolo originale: {{film.original_title}}</h1>
           <h1>Lingua originale: {{film.original_language}}</h1>
           <h1>Voto: {{film.vote_average}}</h1>
   </div>
 </div>

    <div class="tutte-le-serie">
        <h1>SERIE TV TROVATE:</h1>
    <div v-for="(serieTv, index) in serie" :key="index" class="serieList">

        <h1>Titolo: {{serieTv.name}}</h1>
        <h1>Titolo originale: {{serieTv.original_name}}</h1>
        <h1>Lingua originale: {{serieTv.original_language}}</h1>
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
       
    }
    h1{
        margin-bottom: 30px;
    }
    .filmList{
        margin-bottom: 100px;
        
    }
}

</style>