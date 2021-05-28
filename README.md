# Prueba Técnica Servex

El repositorio contine el proyecto que responde al punto número 2 de la prueba técnica asignada por la empresa Servex a Julián Muñoz.

El proyecto consiste en consumir la API de Rick and Morty, esta API contiene la totalidad de los personajes listados con ID del 1
al 671. El proyecto se realizó en VUE.js, tanto para el llamado a la API, la aplicación de filtros y el front.

Se filtraron los primeros 20 ID de los personajes obtenidos de la API. El archivo principal en el que se desarrollo el algoritmo es App.vue.

## Condiciones adicionales aplicadas

- Se presenta el nombre del personaje, status y y especie.
- En caso de que el status del personaje sea "Dead", la imagen se presenta en escala de grises.
- Si el status del peronaje es "Unknown" no muestra el personaje.
- En caso de que el status del personaje sea "Alive", presenta una barra verde en la parte inferior de la caja.
- En caso de que el satus del persona sea "Dead", presenta una barra rojo en la parte inferior de la caja.
- Se contó con repositorio en GITHUB, usando la rama "desarrollo" para el desarrollo del algoritmo, haciendo el posterior merge con la rama master.

Para el desarrollo del proyecto se utilizo:

[GitHub]()

- Node Js para npm v14.17.0 [NodeJS](https://nodejs.org/es/)
- @vue/cli 4.5.13 [VueJs](https://vuejs.org/)

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
