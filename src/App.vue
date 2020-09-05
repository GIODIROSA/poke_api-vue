<template>
  <div id="app">
    
    <Reloj />
    <Navbar />
 <Herosection />

 <div class="container">
    
 <div class="inputPoke form-group mx-sm-3 mb-2">
    <input  v-model="nombre" type="text" class="getpoke form-control" placeholder="Pokemones" @keyup.enter="searchPokemones">
    <button  @click="searchPokemones" class="btn btn-danger">Agregar</button>
    </div>

    <!-- ===========Manejo de error 1====== -->
    <section v-if="errored">
      <p>Lo sentimos, la comunicación se perdido....</p>
    </section>
    <!-- ==========Manejo de error 2=============== -->
    <section v-if="loading">
      <p>Cargando....</p>
    </section>
    <!-- ============================== -->
<!-- contenido-card -->
<div id="content__pokemon">
<div class="card contenido">
  <img :src="imagen" class="card-img-top" alt="imagen">
  <div class="card-body">
    <h1 class="card-title py-2"><strong>{{namePokemon}}</strong></h1>
    <p class="card-text"><strong>height </strong>{{ heightPokemon }}</p>
  </div>
  <ul class="list-group list-group-flush">
    <li class="list-group-item"><strong>Movimientos:</strong></li>
    <li v-for="(moviento, i) in movientos" :key="i" class="list-group-item">{{ moviento.move.name }}</li>
    <li class="list-group-item"><strong>Habilidades:</strong></li>
    <li v-for="(habilidad) in habilidades" class="list-group-item">{{ habilidad.ability.name }}</li>
  </ul>
</div>
</div>
<!-- contenido-card -->
 </div>
  </div>
  
</template>

<script>
import Reloj from './components/Reloj'
import Herosection from './components/Herosection'
import Navbar from './components/Navbar'


export default {
  name: "app",
  data() {
    return {
      nombre: "",
      pokemones: {
        name: "",
        height: "",
        sprites: {
          front_default: "",
        },
        moves: [],
        abilities: [],
      },
      errored: false,
      loading: true,
    };
  },
  created() {
    this.searchPokemones();
  },
  methods: {
    async searchPokemones() {
      try {
        await fetch(this.url)
          .then((response) => response.json())
          .then((data) => {
            console.log(data);
            this.pokemones = data;
          })
          .catch((err) => {
            console.log(`todo esta perdido: ${err}`);
            this.errored = true;
          })
          .finally(()=> this.loading= false)
      } catch (error) {
        console.log(`todo está realmente perdido ${error}`);
      
      }
    
    },
  }, //final de methods
  computed: {
    url() {
      return this.nombre == ""
        ? `${this.baseUrl}pikachu`
        : `${this.baseUrl}${this.nombre.toLowerCase()}`;
    },
    imagen() {
      return this.pokemones.sprites.front_default;
    },
    namePokemon() {
      return this.pokemones.name;
    },
    heightPokemon() {
      return this.pokemones.height;
    },
    movientos() {
      return this.pokemones.moves.slice(0, 10);
    },
    habilidades() {
      return this.pokemones.abilities;
    },
    baseUrl() {
      return "https://pokeapi.co/api/v2/pokemon/";
    },
  }, //final de computed
  components: {
    Reloj,
    Herosection,
    Navbar,
  },//final de components
};
</script>

<style lang="scss" scoped>
.inputPoke{
  margin: 20px 120px;
  display: flex;
  justify-content: center;
  align-content: center;
}
.getpoke{
  width: 500px;
}
.imagen__poke{
  display: block;
  margin: auto;
}
img{
  width: 300px;
}
#content__pokemon{
  display: flex;
  justify-content: center;
  align-content: center;
}
.contenido{
  width: 320px;
}
.card-title{
  text-align: center;
}

</style>
