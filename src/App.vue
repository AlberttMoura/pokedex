<template>
  <div class="app">
    <Nav/>
    <Search @buscar="pesquisarPokemon($event)"/>
    <div class="content">
      <div class="poke" v-for="poke in resultadoBusca" :key="poke.url">
        <Pokemon :nome="poke.name" :url="poke.url"/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Pokemon from "./components/Pokemon"
import Nav from "./components/Nav"
import Search from "./components/Search"


export default {
  name: 'App',

  data() {
    return {
      pokemons: [],
      busca: "",
    }
  },

  components: {
    Pokemon,
    Nav,
    Search,
  },
  methods: {
    pesquisarPokemon: function($event) {
      this.busca = $event.busca
    }
  },

  created: function() {
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=978&offset=0").then(res => {
      this.pokemons = res.data.results
    })
  },
  computed: {
    resultadoBusca: function() {
      if(this.busca == "" || this.busca == " "){
        return this.pokemons
      }
      else{
        return this.pokemons.filter(pokemon => pokemon.name.includes(this.busca.toLowerCase()))
      }
    }
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
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
  grid-template-rows: 15vh auto auto 10vh;
  grid-template-areas: "h h h h h h h"
                       ". s s s s s ."
                       ". c c c c c ."
                       "f f f f f f f";
  width: 100%;
  height: 100%;
}

.content {
  grid-area: c;
  display: grid;
  grid-column: "1fr 1fr 1fr";
  grid-row: "10% 10% 10%";
  grid-template-areas: "x x x";
  width: 100%;
  height: 100%;
}
.poke {
  justify-self: center;
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 3%;
}
</style>
