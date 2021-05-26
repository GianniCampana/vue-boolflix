<template>
  <div id="app">


    ciaooooooooo


  </div>
</template>

<script>
import axios from 'axios';


export default {
  name: 'App',
  components: {

  },
  data(){
    return{
      apiURL: 'https://www.themoviedb.org/3/search/movie',
      apiKey: 'e5d21c27119e25a2e0249ca43680564d',
      query: 'ritorno al futuro'
    }
  },
  created(){
    axios.get(this.apiURL,{
      params:{
        api_key: this.apiKey,
        query: this.query,
        language: 'it-IT'
      }
    })
    .then(resp => {
      console.log(resp.data);
    })
    .catch(err => {
      console.log(err);
    })
  }
}
</script>

<style lang="scss">

</style>
