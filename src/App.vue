<template>

  <div id="app">

    <Header 
    @searchingText= searchingText 
    @searchingTextSerieTV= searchingTextSerieTV 
    />

 

    <Main :films="films" :serie="serie"/>

   

  </div>

</template>

<script>

import axios from 'axios';
import Main from './components/Main'
import Header from './components/Header'


export default {
  name: 'App',
  components: {
    Main,
    Header
  },
  data(){
    return{
      apiURL: 'https://api.themoviedb.org/3/search/movie',
      apiKey: 'e5d21c27119e25a2e0249ca43680564d',
      films: [],

      apiURLSerieTv : 'https://api.themoviedb.org/3/search/tv',
      serie: []
    }
  },
  methods:{

    searchingText(obj){
     this.searching(obj)

    },
    searchingTextSerieTV(obj){
      this.searchingSerieTV(obj)
    },

    searching(query){
      axios.get(this.apiURL,{
        params:{
        api_key: this.apiKey,
        query: query,
        language: 'it-IT'
      }}).then(resp => {
        this.films = resp.data.results
        
      }).catch(err => {
        console.log(err);
      })
    },

    searchingSerieTV(query){
        axios.get(this.apiURLSerieTv,{
        params:{
        api_key: this.apiKey,
        query: query,
        language: 'it-IT'
      }}).then(resp => {
        this.serie = resp.data.results
        
      }).catch(err => {
        console.log(err);
      })
    }
  },
  created(){
    
    
  }
}
</script>
<style lang="scss">
@import './components/general';
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
