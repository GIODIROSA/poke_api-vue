<template>
  <div id="banner">
    <img id="logopoke" src="../assets/img/logo2.png" alt="logo">
    

  </div>
</template>

<script>
export default {
    name: "Herosection",
    data (){
      return{
        titulo: "hola estoy funcionando"
      }
    }

}
</script>

<style lang="scss" scoped>
#banner{
  width: 100%;
  height: 750px;
  background-image: url(../assets/img/03.jpg);
  background-size: cover;
  background-attachment: fixed;
  background-repeat: no-repeat;
 
}
#logopoke{
  display: block;
  margin: auto;
  padding: 100px;
}


</style>