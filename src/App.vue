<template>
  <div id="app">

    <div class="hero is-white is-gradient is-bold">

      <div class="hero-body">
        <h1 class="title">
          <span class="has-text-success">
            Rick And Morty
          </span>
          <span class="subtitle">
            Personajes
          </span>

        </h1>

      </div>


    </div>

    <div class="container">
     <div class="colunms is-desktop is-mobile is-tablet is-multiline is-centered">

       <div class="colunms is-12-mobile is-4-desktop is-4-tablet" v-for="post of posts" v-bind:key="post.id">
      <div class="card">
        <div class="card-header">
          <img v-bind:src="post.image" v-bind:alt="post.name">
    
            <h3><span>Name: </span>{{post.name}}</h3>
            <h3><span>Status: </span>{{post.status}}</h3>
            <h3><span>Species: </span>{{post.species}}</h3>
            
        </div>

        
       </div>


     </div>




      </div>

    </div>



    <!-- <h1>Consultar datos</h1>
    <div class="post" >
      {{ post }}

    </div> -->
 

  </div>
</template>

<script>
import axios from 'axios'
export default {
  dependencies: axios,
  name:'app',
  data(){
    return{
      posts: []
    }
  },
  
  mounted() {
    let vue = this;
    axios.get('https://rickandmortyapi.com/api/character/1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20')
    .then( function( response ) {
        vue.posts = response.data;
    })
  },
  

  
    
  
}
</script>

<style>

</style>
