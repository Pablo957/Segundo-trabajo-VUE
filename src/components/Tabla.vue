<template>
<table class="table">
    <thead class="encabezado">
        <tr>
            <td v-for="nombre in encabezado" :key="nombre">{{nombre}}</td>
        </tr>
    </thead>
    <tbody v-if="!loading">
        <Fila @onClick='avisarAlumno' v-for="alumno in alumnos" :key="alumno.id" :alumno="alumno"/>
    </tbody>
    <img v-if="loading" src="../assets/sp.gif" alt="">
</table>
    
</template>
<script> 
import Fila from './Fila'
export default {
    name:'Tabla',
    components:{
        Fila
    },
    data(){
        return{
            encabezado:[
                'Nombre',
                'Apellido',
                'Edad',
                'Ciudad',
                'Numero de Alumno',
                'Editar',
                'Eliminar'
              ],
        }
    },
    
    props:{
            alumnos:{
                type:Array
            },
              loading:Boolean  
    },
    methods:{
        avisarAlumno(e){
            this.$emit('onClick',e);
        }
    },
    mounted(){
      
    }
}
</script>

<style>
table{
    justify-content: center;
}
.encabezado {
    font-weight: bold;
}
</style>
