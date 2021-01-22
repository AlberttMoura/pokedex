<template>
  <div class="pokemon">
    <img :src="pokemon.img">
    <div>
        <h5>{{ capitalName }} </h5>
        <small>#{{ id }}</small>
        <p>{{ pokemon.types[0] }} {{pokemon.types[1] }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios"

export default {

    created: function() {
        axios.get(this.url).then(res => {
            for(let idx in res.data.types) {
                this.pokemon.types.push(res.data.types[idx].type.name)
            }
            this.pokemon.img = res.data.sprites.front_default
        })        
    },

    data() {
        return {
            pokemon: {
                types: [],
                img: String,
            }
        }
    },

    props:  {
        nome: String,
        id: Number,
        url: String,
    },

    computed: {
        capitalName: function() {
            return this.nome.charAt(0).toUpperCase() + this.nome.slice(1)
        }
    }

}
</script>

<style>
.pokemon {
    justify-self: center;
    justify-items: center;
    justify-content: center;
    text-align: center;
    background-color: #B4B4B4;
    margin: 3%;
    border-radius: 7%;
}
</style>