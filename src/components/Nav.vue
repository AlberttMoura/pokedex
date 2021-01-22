<template>
  <div class="nav">
      <div class="logo-side">
        <a href=""><img id="logo-image" src="../assets/pokedexlogo.png" alt=""></a>
        <a id="logo-text" href="">The Pokedex Project</a>
      </div>
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
    height: auto;
    width: auto;
    text-align: center;
    justify-items: center;
    align-items: center;
    justify-content: space-evenly;
}

#logo-image {
    width: 10vh;
}

.logo-side {
    display: flexbox;
}

#logo-text{
    font-size: 5vh;
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