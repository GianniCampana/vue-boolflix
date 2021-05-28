<template>

    <header>
      <div class="menu">

        <input v-model='searchText' class="input-text" type="text" placeholder="inserisci il film">

        <button 
            class="p-1"
            @click="$emit('searchingText', searchText)">
            <h1>FILM</h1>
        </button>

        <button 
            class="p-1"
            @click="$emit('searchingTextSerieTV', searchText)">
            <h1>SERIE TV</h1>
        </button>

      </div>

    </header>

</template>

<script>
export default {
    name: 'Header',
    
    data(){
        return{
            searchText: ''
        }
    },
    props: {
    },
    methods:{
    }
}
</script>

<style lang="scss" scoped>
.menu{
  width: 100%;
  height: 100px;
  background-color: black;
  display: flex;
  justify-content: center;
  align-items: center;
  button{
      margin-left: 30px;
  }
  input{
    width: 300px;
    height: 30px;
    margin-right: 20px;
  }
}
</style>