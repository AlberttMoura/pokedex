<template>
  <div class="app">
    <div class="content" v-for="(poke, index) in pokemons" :key="index">
      <Pokemon :id="index + 1" :nome="poke.name" :url="poke.url"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Pokemon from "./components/Pokemon"

export default {
  name: 'App',

  data() {
    return {
      pokemons: []
    }
  },

  components: {
    Pokemon,
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
}

.app {
  display: flexbox;
  justify-content: center;
}
</style>
