<template>
  <div id="inicio">
    <h1>Consultar datos</h1>
    <button v:on:click="fetch">Consultar</button>

  </div>
</template>

<script>
import axios from 'axios'
export default {
  dependencies: axios,
  name:'Inicio',
  data(){
    return{
      post: []
    }
  },
  
  mounted() {
    axios.get('https://rickandmortyapi.com/api/character')
    .then( function( response ) {
      console.log(response)
    })
  }
    
  
}
</script>

<style>

</style>
