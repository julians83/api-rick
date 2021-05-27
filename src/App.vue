<template>
  <div id="app">    

    <div class="header">
      <div class="container_title">
        <h1 class="title"> 
            Rick And Morty  
            
        </h1>
        
        <h3 class="subtitle">
           Personajes
        </h3> 
      </div>
      <img class="Img_Header" src="./assets/RM.png" alt="">

         
    </div>

    <div class="container">
     <div class="colunms">

       <div class="card_columns" v-for="post of posts" v-bind:key="post.id">
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

@import url('http://fonts.cdnfonts.com/css/armor-piercing');

html {
    font-size: 62.5%;
    background: #0A123A;
}

::-webkit-scrollbar {
    display: none;
}


* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    -webkit-scrollbar: none;
    outline: none;
}

:root{
  --Titulo: 'Armor Piercing', sans-serif;
  --Azul : #0A123A;
                                                
}

/* Estilos header-------------------------------------------------------------------------- */

.header {
  display: grid;
  justify-items: baseline;
  /* grid-column: 1 / -1; */
  height: 30vh;
  width: 100vw;
  align-items:center;
  /* background: url(./assets/Background.jpg); */
  /* background-position-y: 60%; */
  background: white;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  background-position: cover;
  /* background-attachment: fixed; */
}
.container_title{
  display:grid;
  grid-template-rows: 75% 25%;
}
.container_title .title{
  margin: 0 0 0 25rem;
  font-family: var(--Titulo);
    text-align: inherit;
    font-size: 7rem;
    color: #0A123A;
    transition: all 1.1s ease;
    height: auto;
    padding-top: 2rem;
}

.container_title .subtitle{
  font-size: 4rem;
  font-family: var(--Titulo);
    margin: 0 0 0 25rem;
    color: #0A123A;
    font-weight: 400;
    transition: all ease 0.5s;
    max-width: 40vw;
    opacity: 0.6;
    text-align: inherit;
}

.Img_Header{
  position: relative;
  width: 15rem;
  height:20rem;
  left: 75%;
  top: -69%;
}

/* Estilos contenedor principal-------------------------------------------------------- */

.container{
  display: grid;
  margin: 5rem auto;
  padding: 0rem 5rem;
}

.colunms{
  display: grid;
  grid-template-columns: repeat(3,1fr);
}

/* Estilos de las cards-------------------------------------------------------------------- */

</style>
