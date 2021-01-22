<template>
  <div class="app">
    <Nav/>
    <input class="search" type="text" placeholder="Buscar Pokemon" v-model="busca">
    <div class="content">
      <div class="poke" v-for="(poke, index) in pokemons" :key="index">
        <Pokemon :id="index + 1" :nome="poke.name" :url="poke.url"/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Pokemon from "./components/Pokemon"
import Nav from "./components/Nav"


export default {
  name: 'App',

  data() {
    return {
      pokemons: [],
      busca: '',
    }
  },

  components: {
    Pokemon,
    Nav,
  },

  created: function() {
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then(res => {
      this.pokemons = res.data.results
    })
  }
}
</script>

<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.app {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  grid-template-rows: 15vh 30vh auto 10vh;
  grid-template-areas: "h h h h h"
                       ". s s s ."
                       ". c c c ."
                       "f f f f f";
}

.content {
  grid-area: c;
  display: grid;
  grid-column: "1fr 1fr 1fr";
  grid-row: "10% 10% 10%";
  grid-template-areas: "x x x";
}

.header {
  grid-area: h;
}

.search {
  grid-area: s;
  text-align: center;
  font-size: 3rem;
  margin-top: 15vh;
  margin-bottom: 5vh;
  border-radius: 20px;
  border: 0px;
}

.poke {
  width: auto;
  justify-self: center;
  width: 100%;
  height: 100%;
}
</style>
