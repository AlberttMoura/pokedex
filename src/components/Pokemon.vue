<template>
  <div class="pokemon">
    <div class="card-img">
        <img :src="pokemon.img">
    </div>
    <div id="card">
        <h5>{{ capitalName }} </h5>
        <small>#{{ pokemon.id }}</small>
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
            this.pokemon.id = res.data.id
        })        
    },

    data() {
        return {
            pokemon: {
                types: [],
                img: String,
                id: Number,
            }
        }
    },

    props:  {
        nome: String,
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
    border-radius: 3px;
    width: 100%;
    height: 100%;
    background-color: #f3f3f3

}

.card-img {
    background-color: #E4E4E4;
}

#card h5{
    font-size: 80%;
}

#card p {
    font-size: 70%;
}

</style>