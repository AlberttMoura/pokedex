<template>
  <div class="nav">
    <img id="logo-image" src="../assets/pokedexlogo.png" alt="">
    <a id="logo-text" href="">The Pokedex Project</a>
  </div>
</template>

<script>
export default {

}
</script>

<style>
.nav {
    display: flexbox;
    background-color: #FF2F2F;
    grid-area: h;
    height: 100%;
    width: 100%;
    text-align: center;
    justify-items: center;
    align-items: center;
    justify-content: center;
}

#logo-image {
    height: min(70%, 14vw);
}

#logo-text{
    font-size: min(300%, 9vw);
    font-weight: 100;
    text-decoration: none;
    color: #fff;
}

.menu {
    display: flexbox;
    background-color: red;
    justify-content: space-evenly;

}
</style>