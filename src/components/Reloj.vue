<template>
  <div id="reloj" class="clock py-1 bg-danger">

      <h5><strong>{{getHora}}</strong></h5>


  </div>
</template>

<script>
export default {
    name: "reloj",
    data(){
        return{
            hours: 0,
            minutes: 0,
            segundos: 0,
        }
    },
    created(){
        setInterval(this.actualizacionTime, 1000);
        this.actualizacionTime();
    },
    methods: {
        actualizacionTime(){
            let date= new Date (Date.now());
            this.hours= ('0'+ date.getHours()).slice(-2);
            this.minutes= ('0'+ date.getMinutes()).slice(-2);
            this.segundos= ('0'+ date.getSeconds()).slice(-2);

        },


    },
    computed: {
        getHora(){
            return `${this.hours} : ${this.minutes} : ${this.segundos}`
        }
    }

}
</script>

<style lang="scss" scoped>
.clock{
    display: flex;
    justify-content: center;
    align-content: center;
    color: white;
}

</style>

