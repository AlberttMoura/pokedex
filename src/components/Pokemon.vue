<template>
  <div class="pokemon">
    <div class="card" style="width: 18rem; height: 20rem; border: #B4B4B4 solid 0.6rem; background-color: #B4B4B4;">
        <img :src="pokemon.img"  alt="...">
        <div class="card-body">
            <h5 class="card-title">{{ capitalName }} <br> id: {{ id }}</h5>
            <p class="card-text">{{ pokemon.types[0] }} {{pokemon.types[1] }}</p>
            <a :href="url" class="btn btn-primary">More Info</a>
        </div>
    </div>
  </div>
</template>

<script>
import axios from "axios"

export default {

    created: function() {
        axios.get(this.url).then(res => {
            //console.log(res.data)
            for(let idx in res.data.types) {
                this.pokemon.types.push(res.data.types[idx].type.name)
            }
            this.pokemon.img = res.data.sprites.front_default
            console.log(this.pokemon.img)


            //console.log(this.pokemon.types)
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
    margin-top: 1%;
}

.card-body {
    background-color: #B4B4B4;
}

img {
    background-color: #fff;
    border-radius: 2rem;
    min-height: 20vh;
}
</style>