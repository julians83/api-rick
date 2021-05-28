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
      <img class="Img_Header" src="./assets/RM.png" alt="Img del header" />
    </div>

    <div class="container">
      <div class="colunms">
        <!-- Muestra las tarjetas de los personasjes, recorriendo el array traido de la api por medio del arreglado v-for, 
        usando además como llave el id de los Personajes.
        Se aplica también un filtro en el cual si el status del personaje es 'unknown' la caja tendrá la "unknown" la cual 
        tiene un display none para no mostrar este personaje en la interfaz gráfica-->
        <div class="card_columns" v-for="post of posts" v-bind:key="post.id" :class="post.status === 'unknown' ? 'unknown' : ''">

        <!-- Permite traer la imagen de cada personaje asociada con su id,status y especie además de aplicar un filtro en escala de grises para aquellos
        personasjes que su estatus sea igual a "Dead", esto último se hace por medio de la clase "Sombra" -->
          <div class="card">
            <img v-bind:src="post.image" v-bind:alt="post.name" :class="post.status === 'Dead' ? 'Sombra' : ''"/>
            <h3><span>Name: </span>{{ post.name }}</h3>
            <h3>Status:{{ post.status }}</h3>
            <h3><span>Species: </span>{{ post.species }}</h3>

        <!-- Se filtran los personajes según su status, en caso de que sea igual a "Alive", se asigna una clase "Alive", la cual
        en la parte inferior de la caja permite la visualización de una barra verde; en caso de que el status sea igual a "Dead",
        esta barra será roja -->
            <span :class="post.status === 'Alive' ? 'Alive' : ''"> </span>
            <span :class="post.status === 'Dead' ? 'Dead' : ''"> </span>
          </div>
        </div>
      </div>
    </div>

    <!-- Se utiliza el condicional if para que en caso de que existan errores en el llamado a la API se presente un texto y una imagen 
    de apoyo para informar sobre el mismo -->
    <div v-if="errored">
      <p class="text_error">
        La URL introducida para conectar con la API es errada
      </p>
      <img class="error" src="./assets/Background.jpg" alt="Img de error" />
    </div>
  </div>
</template>

<script>
// Se importa Axios, el cual es un cliente HTTP basado en promesas para JS, este cliente permite realizar la petición a la API por medio
// del metodo GET
import axios from "axios";
export default {
  // Esta función retorna los valores obtenidos de la API por medio de metodo GET, almacenandolos en una lista con el nombre posts
  data: function() {
    return {
      posts: [],
      loading: true,
      errored: false,
    };
  },

  mounted() {
    let vue = this;
    // Se utliza el metodo GET para hacer el llamado a la API por medio del cliente axios, la URL contiene los números del 1 al 20,
    // esto permite solicitarle a la API solo los 20 primeros ID de la lista.
    axios.get(
        "https://rickandmortyapi.com/api/character/1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20"
      )
    //Con .then se recibe la respuesta de la API y posterior mente se almacena en posts.
      .then(function(response) {
        vue.posts = response.data;
      })
    //Se controlan los errores derivados del llamado a la API y se genera una alerta que contiene instrucciones y el código del error
      .catch((error) => {
        alert(
          "No se puede consultar la API, revisa la URL introducida\n" + error
        );
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },
};
</script>


<style>

@import url("http://fonts.cdnfonts.com/css/armor-piercing");

html {
  font-size: 62.5%;
  background: #0a123a;
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

:root {
  --Titulo: "Armor Piercing", sans-serif;
  --Azul: #0a123a;
}

/* Estilos header-------------------------------------------------------------------------- */

.header {
  justify-items: baseline;
  height: 30vh;
  width: 100vw;
  align-items: center;
  background: white;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  background-position: cover;
}
.container_title {
  display: grid;
  grid-template-rows: 75% 25%;
}
.container_title .title {
  margin: 2rem 0 0 15%;
  font-family: var(--Titulo);
  text-align: inherit;
  font-size: 7rem;
  color: #0a123a;
  transition: all 1.1s ease;
  height: auto;
  padding-top: 2rem;
}

.container_title .subtitle {
  font-size: 4rem;
  font-family: var(--Titulo);
  margin: 0 0 0 25rem;
  color: #0a123a;
  font-weight: 400;
  transition: all ease 0.5s;
  max-width: 40vw;
  opacity: 0.6;
  text-align: inherit;
}

.Img_Header {
  position: relative;
  width: 25rem;
  height: 20rem;
  left: 75%;
  top: -73%;
}

/* Estilos contenedor principal-------------------------------------------------------- */

.container {
  display: grid;
  margin: 5rem auto;
  padding: 0rem 5rem;
}

.colunms {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

/* Estilos de las cards-------------------------------------------------------------------- */

.card_columns {
  justify-self: center;
  color: white;
  border-radius: 2rem;
  margin-bottom: 4rem;
  padding: 2rem;
  transition: 0.6s;
  /* background:#233567; */
  background: #233567;
  box-shadow: 1px 1px 5px #1e2d58, -1px -1px 5px #283d76;
}

.card_columns:hover {
  transform: scale(1.05);
  transition: ease 0.6s;
  background: linear-gradient(145deg, #20305d, #25396e);
  box-shadow: 15px 15px 30px #1e2d58, -15px -15px 30px #283d76;
}

.card {
  font-family: "Segoe UI";
  font-size: 1.8rem;
}

.card img {
  border-radius: 2rem;
}

/* Estilos aplicados a los filtros ALive y Dead */
.Alive {
  margin: 1rem;
  display: flex;
  border-width: 0.3rem;
  border-style: solid;
  color: green;
  border: solid;
  /* width: 100%; */
}

.Dead {
  display: flex;
  margin: 1rem;
  border-width: 0.3rem;
  border-style: solid;
  color: red;
  border: solid;
}

.unknown {
  display: none;
}

.Sombra {
  filter: grayscale(100%);
}

.Sombra:hover {
  filter: none;
  border: 3px solid red;
}

/* Estilos de la imagen y texto asociado al error */
.error {
  width: 50%;
  height: 50%;
  margin: 0 25%;
  border-radius: 3rem;
  box-shadow: 20px 20px 60px #233567, -20px -20px 60px #233567;
}

.text_error {
  font-family: var(--Titulo);
  color: white;
  font-size: 4rem;
  text-align: center;
}

/* Estilos Movil----------------------------------------------------------------- */

@media (max-width: 750px) and (min-width: 240px) {
  .container_title .title {
    margin: 2rem 0 0 5%;
    font-size: 7rem;
    color: #0a123a;
  }

  .container_title .subtitle {
    font-size: 4rem;
    margin: 0 0 0 10%;
  }

  .container {
    display: grid;
    margin: 5rem auto;
    padding: 0rem;
  }
  .container_title {
    display: grid;
    grid-template-rows: 100%;
  }

  .colunms {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
  }

  .card_columns {
    padding: 1rem;
  }

  .Img_Header {
    position: relative;
    width: 20rem;
    height: 15rem;
    left: 56%;
    top: -33%;
  }
}

/* Estilos Tablet----------------------------------------------------------------- */

@media (max-width: 1024px) and (min-width: 701px) {
  .colunms {
    grid-template-columns: repeat(2, 1fr);
    column-gap: 2rem;
  }

  .Img_Header {
    display: none;
  }

  .container_title .title {
    margin: 4% 0 0 10%;
    font-size: 7rem;
    color: #0a123a;
  }

  .container_title .subtitle {
    font-size: 4rem;
    margin: 1rem 0 0 10%;
  }
}
</style>
