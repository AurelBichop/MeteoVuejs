<template>
  <div class="container">
    <h1 class="my-4">App Meteo avec Vue Js</h1>

    <div class="form-group mb-5">
      <label for="position">Entrer le nom d'un Ville</label>
      <input 
        type="text" 
        class="form-control" 
        id="position"
        v-model="requete"
        v-on:keypress="goMeteo"
      >
    </div>

    <div class="w-75 m-auto" v-if="temps">
      <h3 class="text-center mb-3">
        Position: {{temps.name}}
      </h3>
      <div class="card text-center p-5">
        <p class="texte-affichage">
          Température : {{temps.main.temp.toFixed()}} °C
        </p>
        <p class="texte-affichage">
          Temps: {{temps.weather[0].description}}
        </p>
      </div>
    </div>
  </div>
  
</template>

<script>

import axios from 'axios'

export default {
  name: 'Meteo',
  data(){
    return{
      requete:'',
      temps: undefined,
      api_code: 'ApI Key',
      url_recherche: 'https://api.openweathermap.org/data/2.5/weather?'
    }
  },
  methods:{
    goMeteo(e){
      if(e.key == 'Enter'){
        axios
          .get(`${this.url_recherche}q=${this.requete}&units=metric&APPID=${this.api_code}&lang=fr`)
          .then(reponse => {
            //console.log(reponse)
            this.temps = reponse.data;
          })
          this.requete = ''
      }
    }
  }
}
</script>

<style>
.texte-affichage{
  font-size: 30px;
  font-weight: 300;
  line-height: 1.2;
}
</style>
