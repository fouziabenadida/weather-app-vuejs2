<template>
  <div class="container">
    <h1 class="my-4">Weather App With Vue.js 2</h1>

    <div class="form-group mb-5">
      <label for="position">Enter The Name Of a City</label>
      <input
        type="text"
        id="position"
        class="form-control"
        v-model="requete"
        @keypress.enter="goMeteo"
      />
    </div>
    <div class="w-75 m-auto" v-if="temps">
      <h3 class="text-center mb-3">Position: {{temps.name}} </h3>
      <div class="card text-center p-5">
        <p class="texte-affichage">Temperature: {{temps.main.temp.toFixed()}} &#176;</p>
        <p class="texte-affichage">Humidity: {{temps.main.humidity}}</p>
        <p class="texte-affichage"> Weather: {{temps.weather[0].description}}</p>
      </div>
    </div>
  </div>
</template>



<script>
import axios from 'axios'


export default {
  name: "meteo-app",
  data() {
    return {
        requete: '',
        temps: undefined,
        api_code:'affc15e769a92157172eca0fe26b82d1',
        url_recherche: 'https://api.openweathermap.org/data/2.5/weather?'
    };
  },
  methods: {
  goMeteo() {
    axios
    .get(`${this.url_recherche}q=${this.requete}&units=metric&APPID=${this.api_code}&lang=en`)
    .then(response=> {
        console.log(response)
        this.temps= response.data
        console.log(this.temps)
    })
    this.requete= ''
  }
  },
};
</script>



<style scoped>
h1{
    text-align: center;
    font-size: 30px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    letter-spacing: 3;
    line-height: 30px;
    font-weight: 300;
    padding: 20px;

}
label{
    font-family: Arial, Helvetica, sans-serif;
    font-size: 13px;
    padding-bottom: 5px;
}
.texte-affichage{
    font-size: 30px;
    font-weight: 300;
    line-height: 1.2;
}
</style>