<template>

  <div id="app">
      <Header 
      @searchingText= searchingText 
      @searchingTextSerieTV= searchingTextSerieTV 
      @searchingTextAll= searchingTextAll
      />
      <Main :films="films" :serie="serie"/>
      
  </div>

</template>

<script>

  import axios from 'axios';
  import Main from './components/Main';
  import Header from './components/Header';

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
        apiURLSerieTv : 'https://api.themoviedb.org/3/search/tv',
        films: [],
        serie: [],
        searchText: ''
      }
    },

  methods:{

    searchingText(obj){
     this.searching(obj)
    },

    searchingTextSerieTV(obj){
      this.searchingSerieTV(obj)
    },
    searchingTextAll(obj){
      this.searchingAll(obj)
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
      return this.films
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
      return this.serie
    },
   
     searchingAll(query){
      this.searching(query)
      this.searchingSerieTV(query)
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
#app{
  background-color: black;
}
</style>
