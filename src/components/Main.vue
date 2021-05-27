<template>
  <div class="main">

   <h1>FILM TROVATI</h1>
   <div v-for="(film, index) in films.results :key=index" class="filmList">

   </div>

  </div>
</template>

<script>
export default {
    name: 'Main',
    props:{
     films: 
    }
    
}
</script>

<style lang='scss' scoped>

.main{
    width: 100%;
    height: 100vh;
    background-color: gray;
}

</style>