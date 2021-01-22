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
    height: 70%;
}

.logo-side {
    display: flexbox;
    text-align: center;
    align-items: center;
    align-self: center;
    width: 100%;
    height: 100%;
}

#logo-text{
    font-size: max(200%, 4vw);
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