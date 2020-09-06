<template>
  <div id="reloj" class="clock py-1 bg-danger">
    <h5>
        <!-- pintar en pantalla -->
      <strong>{{ getHora }}</strong>
    </h5>
  </div>
</template>

<script>
export default {
  name: "reloj",
  data() {
    return {
      hours: 0,
      minutes: 0,
      segundos: 0,
    };
  },
  created() {
      //antes del mountes cargar la obtención de la data y posterior incluir setInterval para la actualización, segundo a segundo
    setInterval(this.actualizacionTime, 1000);
    this.actualizacionTime();
  },
  methods: {
      //carga de la data de tiempo
    actualizacionTime() {
      let date = new Date(Date.now());
      //extracción de la data: horas, minutos y segundo
      this.hours = ("0" + date.getHours()).slice(-2);
      this.minutes = ("0" + date.getMinutes()).slice(-2);
      this.segundos = ("0" + date.getSeconds()).slice(-2);
    },
  },
  computed: {
      //retornar horas, minutos y segundos para la pintar en pantalla
    getHora() {
      return `${this.hours} : ${this.minutes} : ${this.segundos}`;
    },
  },
};
</script>

<style lang="scss" scoped>
//configuración del reloj en pantalla
.clock {
  display: flex;
  justify-content: center;
  align-content: center;
  color: white;
}
</style>
