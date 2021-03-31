<template>
    <div class="card" style="width: 18rem;">
        <div class="card-body">
             <h5 class="card-title"> {{participante.nombre}}</h5>
             <p class="card-text" v-if="mostrarDiv">{{participante.descripcion}}</p>
             <button class="btn btn-primary" @click="reflejarDiv">Conocenos</button>
        </div>
    </div>
</template>
<script>
export default {
  name: 'Card',
  data () {
    return {
      mostrarDiv: false
    }
  },
  methods:{
        reflejarDiv(){
              this.mostrarDiv=true
        }
    },
  props: {
    participante: {
      type: Object
    },
  }
}
</script>

<style scoped>
.card {
    margin: 12%;
}
</style>