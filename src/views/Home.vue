<template>
  <div class="home">
   <Card class="container" v-for="participante in participantes" :key="participante.id" :participante='participante'></Card>
  </div>
</template>
<script>
import Card from '@/components/Card'
export default {
  name: 'Home',
  components: {
    Card
  },
  data: function () {
    return {
      participantes: [
        {
          nombre:'Pablo Bracciale', 
          descripcion:'Mi nombre es Pablo Bracciale, edad de treinta y cinco años. Soy casado y tengo una hija de dos años'
        },
        {
          nombre:'Gabriel Penna', 
          descripcion:'Mi nombre es Gabriel Pena, edad de treinta y ocho años. Soy casado y encargado en empresa de aberturas'
        }
    ]
    }
  },
  methods: {
    reflejarDiv() {
}
  }
}
</script>

<style scoped>
.home {
  background-color: grey;
  height: 100vh;
	overflow: hidden;
	width: 100%; 
}
.container {
	float: left;
}
</style>
