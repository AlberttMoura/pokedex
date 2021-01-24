<template>
  <div class="app">
    <Nav/>
    <Search @buscar="pesquisarPokemon($event)"/>
    <div class="content">
      <div class="poke" v-for="poke in resultadoBusca" :key="poke.url">
        <Pokemon :nome="poke.name" :url="poke.url"/>
      </div>
    </div>
    <div id="showmore">
      <input @click="mostrarMais" type="button" value="Mostrar Mais">
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
      pokelist: [],
      pokemonsAll: [],
      busca: "",
      initial: 0,
      range: 18,
      pokeCache: [],
      maxPoke: 988,
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
    },

    mostrarMais: function() {
      if(this.range != 0){
        this.initial += this.range
        this.initial + this.range <= this.maxPoke ? this.range = 18 : this.range = this.maxPoke - this.initial
        
        this.getPokemons()
        
      }
    },

    getPokemons: function() {
      for(let i = this.initial; i < this.initial + this.range; i++) {
        this.pokeCache.push({"name": this.pokemonsAll[i].name, "url": this.pokemonsAll[i].url})
        //console.log(this.pokemonsAll[i].name)
        //console.log(i)
      }
    },
    loadAllPokemons: function() {
      axios.get(`https://pokeapi.co/api/v2/pokemon?limit=${this.maxPoke}&offset=${this.initial}`).then(res => {
        let temp = res.data.results
        for(let poke in temp){
          this.pokemonsAll.push({"name": temp[poke].name, "url": temp[poke].url})
        }
        this.getPokemons()
      })
    },
    makePokeList: function() {
      if(this.busca == "" || this.busca == " "){
        this.pokelist = this.pokeCache
      }
      else{
        this.pokelist = this.pokemonsAll.filter(pokemon => pokemon.name.includes(this.busca.toLowerCase()))
      }
      return this.pokelist
    }
  },

  created: function() {
    this.loadAllPokemons()
    
  },
  computed: {
    resultadoBusca: function() {
      return this.makePokeList()
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
  grid-template-rows: max(10vh, 100px) auto auto 10vh;
  grid-template-areas: "h h h h h h h"
                       ". s s s s s ."
                       "c c c c c c c"
                       ". m m m m m ."
                       "f f f f f f f";
  width: 100%;
  height: 100%;
  margin-bottom: min(20%, 10vh);
  
}

.content {
  grid-area: c;
  display: grid;
  grid-template-areas: "x x x";
  width: 100%;
  height: 100%;
  padding-right: 3%;
  padding-left: 3%;
}
.poke {
  justify-self: center;
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding: 3%;
}

#showmore {
  padding-top: min(15%, 7vh);
  grid-area: m;
  text-align: center;
}

#showmore input {
  border: 0px;
  background-color: #58B863;
  border-radius: 10px;
  height: min(2.5rem, 40px);
  font-weight: 500;
  width: min(150px, 25vw);
  font-size: 100%;
  color: #fff;
  outline: none;
}

</style>
