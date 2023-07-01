<template>
  <div id="main">

    <div class="tittle">

      <h1 class="title" v-if="tempe">{{ tempe.temp }} °C</h1>



    </div>
    <div class="subsession">

      <h1 class="subtitle" v-if="describe">{{ describe.description }}</h1>

    </div>


    <div class="leftSession">

      <ol class="listOne">

        <li v-if="cidade">{{ cidade.city }}</li>

       <li v-if="rain">Probabilidade de chuva: {{ rain[0].rain_probability }}%</li>

       <li v-if="nebu">Nebulosidade: {{nebu.cloudiness}}%</li>

        <li v-if="humi">Humidade: {{ humi.humidity  }}%</li>

        <li v-if="velo">Velocidade do vento: {{ velo.wind_speedy }}</li>

      </ol>

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
            describe: null,
            rain: [],
            nebu: null,
            humi: null,
            velo: null,
        }
    },

    methods:{


     async GetApi(){

        try{
            const key = "135efbc7";
            const res =  await axios.get(`https://api.hgbrasil.com/weather?format=json-cors&key=${key}&lat=-&lon=-&user_ip=remote`)

            this.tempe = res.data.results;
            this.cidade = res.data.results;
            this.describe = res.data.results;
            this.rain = res.data.results.forecast;
            this.nebu = res.data.results;
            this.humi = res.data.results;
            this.velo = res.data.results;


            console.log("API rodando...")

        }catch(error) {
            console.log("Houve Erro na Aplicação " + error)
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
margin-bottom: 50px;
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

.listOne{
  color: #fff;
  font-size: 28px;
}

.leftSession{
  display: flex;
  justify-content: flex-start;
  margin-top:110px;
  margin-left:28px;
}

li{
  margin-bottom: 22px;
}

@media (max-width: 1740px){
  
  #main{
    width: 1560px;
  }

}

@media (max-width: 1610px){

  #main{
    width:1380px;
  }

}

@media (max-width: 1450px){

  #main{
    width: 1190px;
  }

}

@media (max-width: 1270px){

  #main{
    width: 995px;
  }

}

@media (max-width: 1051px){

  #main{
    width: 800px;
  }

}

@media (max-width: 833px){

  #main{
    width: 670px;
  }

}

@media (max-width: 700px){

  #main{
    width: 560px;
  }

}

@media (max-width: 587px){

  #main{
    width: 500px;
  }

}


@media (max-width: 548px){

  #main{
    width: 470px;
    height: 565px;
  }
  .listOne{
    font-size: 24px;
  }
  .subtitle{
    font-size: 27px;
  }
  .tittle{
    font-size: 60px;
  }

}

@media(max-width: 500px){

  .session{
    margin-top: 48px;
  }
  .listOne{
    font-size: 21px;
  }
  .subtitle{
    font-size: 24px;
  }
  .title{
    font-size: 61px;
  }

  #main{
    width: 410px;
  }

}

@media(max-width: 435px){

  #main{
    width:365px;
  }
  .listOne{
    font-size: 20px;
  }
  .subtitle{
    font-size: 23px;
  }
  .title{
    font-size: 55px;
  }
  .leftSession{
    margin-left: 20px;
  }

}

@media (max-width: 379px){

  #main{
    width: 295px;
  }
  .listOne{
    font-size: 18px;
  }

}

@media (max-width: 314px){

  .title{
    font-size: 49px;
  }
  .subtitle{
    font-size: 21px;
  }
  .listOne{
    font-size: 17px;
  }
  .leftSession{
    margin-left: 13px;
  }
  #main{
    width: 275px;
    height: 500px;
  }


}

@media(max-width:287px){
  .listOne{
    font-size: 16px;
  }
  #main{
    width:250px;
  }
}

@media(max-width:260px){
  #main{
    width:230px;
  }
  .listOne{
    font-size: 14px;
  }
  .subtitle{
    font-size: 19px;
  }
  .title{
    font-size: 45px;
  }
}

@media(max-width:243px){
  #main{
    width:210px;
    height: 438px;
  }
  .listOne{
    font-size: 13px;
  }
  .leftSession{
    margin-top:78px;
  }
}

</style>