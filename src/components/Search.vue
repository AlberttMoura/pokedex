<template>
  <div class="search">
      <input class="search-bar" type="text" placeholder="Buscar Pokemon" v-model="busca">
      <input @click="buscarPokemon" class="search-button" type="button" value="Buscar">
  </div>
</template>

<script>
export default {
    data() {
        return {
            busca: ""
        }
    },
    props: {

    },
    methods: {
        buscarPokemon: function () {
            this.$emit("buscar", {busca: this.busca})
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

.search {
    grid-area: s;
    justify-content: center;
    text-align: center;
    min-height: 16rem;
}

.search-bar {
  text-align: center;
  font-size: 3rem;
  border: 0px;
  width: 100%;
  border-radius: 20px;
  margin-top: 5rem;
  margin-bottom: 5vh;
}

.search-button {
    width: 20%;
    border-radius: 10px;
    border: 0px;
    background-color: #58B863;
    height: 2rem;
    color: #fff;
    font-weight: 500;
}

</style>