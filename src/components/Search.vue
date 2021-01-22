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
    min-height: max(14rem, 30vh);
    width: 100%;
    height: 100%;
    margin-bottom: 4%;
}

.search-bar {
  text-align: center;
  border: 0px;
  width: 100%;
  height: 30%;
  border-radius: 20px;
  margin-top: max(11vh, 6%);
  font-size: 200%;
  margin-bottom: max(5vh, 6%);
}

.search-button {
    width: max(15%, 15vw);
    border-radius: 10px;
    border: 0px;
    background-color: #58B863;
    height: 12%;
    color: #fff;
    font-weight: 500;
    font-size: 110%;
    outline: none;
}

</style>