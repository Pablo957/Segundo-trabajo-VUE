<template>
    <div>
        <input v-model="nombre" type="text" placeholder="Nombre" @input="$v.nombre.$touch()">
        <input v-model="apellido" type="text" placeholder="Apellido">
        <input v-model="edad" type="number" placeholder="Edad">
        <input v-model="ciudad" type="text" placeholder="Ciudad">
        <input v-model="nroAlumno" type="number" placeholder="Numero de alumno">
        <Boton @onClick="mandarEvento" titulo="Aceptar"/>
        <Boton @onClick="mandarEvento" titulo="Cancelar"/>
    </div>
</template>
<script> 
import Boton from './Boton';
import { required, numeric } from 'vuelidate/lib/validators'
export default {
    name:'Formulario',
    components:{
        Boton
    },
    data(){
        return{
            nombre:this.alumnoSeleccionado.nombre,
            apellido:this.alumnoSeleccionado.apellido,
            edad:this.alumnoSeleccionado.edad,
            ciudad:this.alumnoSeleccionado.ciudad,
            nroAlumno:this.alumnoSeleccionado.nroAlumno,
            errores:[]
        }
    },
    validations: {
        nombre: {
            required
        },
        edad: {
            required,
            numeric
        }
    },
    methods:{
        mandarEvento(e){
             let alumnoSeleccionado = {
                nroAlumno: this.nroAlumno,
                nombre: this.nombre,
                apellido: this.apellido,
                edad: this.edad,
                ciudad: this.ciudad,
            };      
            this.$emit('onClick',{alumnoSeleccionado,titulo:e});
        }
    },
    props:{
        alumnoSeleccionado:{
            type:Object
        }
    },
    mounted(){
        
    }
}
</script>