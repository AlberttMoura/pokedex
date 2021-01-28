<template>
  <div class="search">
      <input class="search-bar" type="text" placeholder="Buscar Pokemon" v-model="busca"><br>
      <input @click="buscarPokemon" class="search-button" type="button">
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
    width: 100%;
    height: 100%;
    background-color: #303030;
    padding-top: 3%;
    padding-bottom: 3%;
    display: flex;
    border-bottom: #494949 10px solid;
    box-sizing: border-box;
}

.search-bar {
  text-align: center;
  border: 3px #616161 solid;
  border-radius: 5px;
  font-size: 150%;
  outline: none;
  width: 60%;
  height: 48px;
  align-self: center;
  margin-right: 2%;
}

.search-button {
    border-radius: 100%;
    text-align: center;
    border: 0;
    height: 48px;
    width: 48px;
    background-image: url('../assets/searchicon.png');
    outline: none;
    align-self: center;
}

</style>