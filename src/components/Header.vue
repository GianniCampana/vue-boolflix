<template>

<header>
    <div class="menu">
          
        <div class="input-btn">
            <input v-model.trim='searchText' class="input-text" type="text" 
                placeholder="inserisci il film" 
                @keyup.enter="$emit('searchingTextAll', searchText), addEmptyString()" > 

            <div
                class="p-1"
                @click="$emit('searchingTextAll', searchText), addEmptyString()">
                CERCA
            </div>

            <div 
                class="p-1"
                @click="$emit('searchingText', searchText), addEmptyString()">
                FILM
            </div>

            <div 
                class="p-1"
                @click="$emit('searchingTextSerieTV', searchText) , addEmptyString()">
                SERIE TV
            </div>
        </div>

        <div class="logoB">
            Boolflix
        </div>
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
        addEmptyString(){
            this.searchText= ''
        }
    }
}
</script>

<style lang="scss" scoped>
header{
    width: 100%;
    height: 90px;
    position: relative;
        .menu{
            width: 100%;
            height: 90px;
            background-color: #000000;
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
            padding-left: 30px;
            position: fixed;
            top: 0%;
            z-index: 2;
                .input-btn{
                    width: 50%;
                    height: 90px;
                    display: flex;
                    justify-content: space-around;
                    align-items: center;
                        input{
                            background-color: rgb(214, 210, 210);
                            width: 350px;
                            height: 30px;
                            border-radius: 5px;
                            margin-right: 25px;
                            padding-left: 10px;
                            padding-top: 17px;
                            padding-bottom: 17px;
                        }
                        input:focus{
                            outline: none;
                        }
                        div{
                            width: 80px;
                            height: 40px;
                            margin-right: 25px;
                            color: white;
                            background-color: rgb(68, 68, 68);
                            display: flex;
                            justify-content: center;
                            align-items: center;
                            border-radius: 10px;
                            cursor: pointer;
                            border: solid 1px rgb(150, 150, 150);
                        }
                        div:hover{
                            background-color: rgb(105, 105, 105);
                        }
                }
                .logoB{
                    background-image: linear-gradient(to right, #770000 20%, #000000 100%);
                    padding-bottom: 10px;
                    transform: rotateY(180deg);
                    color: black;
                    width: 50%;
                    height: 90px;
                    font-size: 100px;
                    display: flex;
                    align-items: center; 
                }
        }
}


</style>