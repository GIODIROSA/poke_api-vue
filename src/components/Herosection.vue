<template>
  <div id="banner">
    <!-- imagen para el desarrollo de parallax -->
    <img id="logopoke" src="../assets/img/logo2.png" alt="logo" />
  </div>
</template>

<script>
export default {
  name: "Herosection",
 
};
</script>

<style lang="scss" scoped>
//configuracion del banner y parallax
#banner {
  width: 100%;
  height: 750px;
  background-image: url(../assets/img/03.jpg);
  background-size: cover;
  background-attachment: fixed;
  background-repeat: no-repeat;
}
//configuracion del logo
#logopoke {
  display: block;
  margin: auto;
  padding: 100px;
}
</style>
