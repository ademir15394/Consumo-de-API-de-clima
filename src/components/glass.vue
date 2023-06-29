<template>
  <div id="main">

    <div class="tittle">

      <h1 class="title" v-if="texto">{{ texto.temp }}°C</h1>

    </div>


  </div>
</template>

<script>
import axios from "axios"

export default {
    name: "glass",


    data(){
        return{
            texto: null
        }
    },

    methods:{


     async GetApi(){

        try{
            const key = "135efbc7";
            const response =  await axios.get(`https://api.hgbrasil.com/weather?format=json-cors&key=${key}&lat=-&lon=-&user_ip=remote`)

            this.texto = response.data.results;

        }catch(error) {
            console.log("Houve Erro na Aplicação" + error)
        }

    },

},

created() {
    this.GetApi();
  }
};


</script>

<style scoped>
@import "../assets/main.css";

#main{
width: 1700px;
height: 700px;
background: rgb(38, 38, 38);
border-radius: 34px;
}

.tittle{
  display:flex;
  justify-content: center;
  margin-top: 30px;
}

.title{

  font-size: 60px;



}

</style>