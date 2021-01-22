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
    width: 100%;
    height: 100%;
}

.search-bar {
  text-align: center;
  font-size: 3rem;
  border: 0px;
  width: 100%;
  height: 30%;
  border-radius: 20px;
  margin-top: 10%;
  margin-bottom: 5%;
}

.search-button {
    width: 15%;
    border-radius: 10px;
    border: 0px;
    background-color: #58B863;
    height: 12%;
    color: #fff;
    font-weight: 500;
    font-size: 110%;
}

</style>