<template>
    <tr>
        <td>{{alumno.nombre}}</td>
        <td>{{alumno.apellido}}
        <td>{{alumno.edad}}</td>
        <td>{{alumno.ciudad}}</td>
        <td>{{alumno.nroAlumno}}</td>
        <td><Boton @onClick='avisarTabla' titulo='Editar'/></td>
        <td><Boton @onClick='avisarTabla' titulo='Eliminar'/></td>
        </tr> 
</template>
<script> 
import Boton from './Boton'
export default {
    name:'Fila',
    components:{
        Boton
    },
    data(){
        return{
        }
    },
    methods:{
        avisarTabla(e){
            this.$emit('onClick', {alumno:this.alumno,titulo:e});
        }
    },
    props:{
        alumno:{
            type:Object
        }
    },
    mounted(){
        
    }
}
</script>