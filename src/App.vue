<template>

  <div id="app">
    <Header @searchingText='searchingText' />
    <Main />
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
     
      
    }
  },
  methods:{

    searchingText(obj){
     this.searching(obj)

    },

    searching(query){
          axios.get(this.apiURL,{
            params:{
            api_key: this.apiKey,
            query: query,
            language: 'it-IT'
          }
    })
    .then(resp => {
      console.log(resp);
    })
    .catch(err => {
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
