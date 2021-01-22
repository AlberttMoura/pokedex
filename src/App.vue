<template>
  <div class="app">
    
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',

  data() {
    return {
      pokemons: []
    }
  },

  components: {

  },

  created: function() {
    console.log(axios)
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
</style>
