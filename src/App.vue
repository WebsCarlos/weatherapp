<template>
  <div>
    <section>
      <input type="text" v-model="city" placeholder="Busca una ciudad">

      <button name="search" v-on:click="query" >Go!</button>

      <h1>{{result.location.name}}</h1>
      <h2>{{result.current.temp_c}}º</h2>
      <h3>{{result.current.condition.text}}</h3>
      <img v-bind:src="result.current.condition.icon" alt="icono" />
      
    </section>


    <WeatherFooter :result="result"/>
  </div>
</template>




<script>
import axios from "axios";
import WeatherFooter from '../src/components/footer.vue';
// import {getWeatherFrom} from '../src/weather.js'

// const weatherPromise = getWeatherFrom();

export default {
  name: 'App',
   components: {
    WeatherFooter,
  },
  data: () => ({
    result: [],
    city: ""
  }),
  methods:{
    query : function(){
      axios.get('https://api.weatherapi.com/v1/current.json?key=f945fadb20504229a71175609222107&q='+ this.city +'&aqi=yes')
      .then((result) => {this.result = result.data})
      console.log(this.result)
    }
  },
  created(){
      axios.get('https://api.weatherapi.com/v1/current.json?key=f945fadb20504229a71175609222107&q=Barcelona&aqi=yes')
      .then((result) => {this.result = result.data})
  }
}

</script>