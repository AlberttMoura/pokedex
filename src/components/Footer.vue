<template>
  <div class="footer">
      <div class="right">
          <p>ThePokedexProject&reg; 2021</p>
      </div>
      <div class="left">
          <p>Contact: +55 0 1234-5678</p>
      </div>
  </div>
</template>

<script>
export default {

}
</script>

<style>
.footer {
    grid-area: f;
    background-color: #303030;
    color: #fff;
    display: flex;
    justify-content: space-between;
    height: 100%;
    width: 100%;
    bottom: 0%;
    margin: 0;
    padding-right: 2%;
    padding-left: 2%;
    position: relative;
}

.right {
    align-self: center;
    font-size: max(100%, 1.2vw);
}

.left {
    align-self: center;
    font-size: max(100%, 1.2vw);
}
</style>