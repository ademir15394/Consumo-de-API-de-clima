<template>
  <div id="main">

    <div class="tittle">

      <h1 class="title" v-if="tempe">{{ tempe.temp }} °C</h1>



    </div>
    <div class="subsession">
      <h1 class="subtitle" v-if="describe">{{ describe.description }}</h1>
    </div>

  </div>
</template>

<script>
import axios from "axios"

export default {
    name: "glass",


    data(){
        return{
            tempe: null,
            cidade: null,
            describe: null
        }
    },

    methods:{


     async GetApi(){

        try{
            const key = "135efbc7";
            const response =  await axios.get(`https://api.hgbrasil.com/weather?format=json-cors&key=${key}&lat=-&lon=-&user_ip=remote`)

            this.tempe = response.data.results;
            this.cidade = response.data.results;
            this.describe = response.data.results;

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
  margin-top: 20px;
}

.title{
  color:#fff;
  font-size: 70px;
  display: flex;
  text-align: center;
  font-weight: lighter;

  background-image: linear-gradient(52deg, rgba(236,140,226,1) 19%, rgba(57,75,231,1) 94%);
  /* agora colocamos o fundo gradiente dentro do texto com essa propriedade */
  background-clip: text;
  -webkit-background-clip: text;
  /* a cor do texto deve estar como transparent */
  color: transparent;

}

.subsession{
  display: flex;
  justify-content: center;
  margin-top:22px;
}
.subtitle{
  font-size: 30px;
  color:#fff;
  font-weight: normal;
}

</style>