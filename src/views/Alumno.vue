<template>
    <div class="alumno">
        <Boton class="btnagregar" @onClick="clickAgregar" titulo="Agregar"/>
        <Tabla @onClick='obtenerFila' :alumnos='alumnos'/>
        <Formulario v-if="mostrarFormulario" :alumnoSeleccionado='alumnoSeleccionado' @onClick="obtenerInfoFormulario"/>
    </div>
</template>

<script> 
import Tabla from '../components/Tabla'
import Formulario from '../components/Formulario'
import Boton from '../components/Boton'
export default {
    name:'Alumno',
    components:{
        Tabla,Formulario,Boton
    },
    data(){
        return{
        alumnos:[], 
        alumnoSeleccionado:{},
        mostrarFormulario:false,
        opcion: 0,
        loading:false
        }
    },
    methods:{
        obtenerAlumnos(){
            this.loading=true;
            fetch('https://phs-class-api.herokuapp.com/alumno?numeroGrupo=4',{
            method:'GET',
            headers:{"Content-Type": "application/json"},})
                .then((r)=>{r.json()
                .then((data)=>{
                this.loading=false;
                this.alumnos=data.resultado;
                })
            })
        },
        crearAlumno(e){
            fetch('https://phs-class-api.herokuapp.com/alumno?numeroGrupo=4',{
            method:'POST',
            headers:{"Content-Type": "application/json"},
                body: JSON.stringify(e)})
                .then((r)=>{r.json()
                .then(()=>{
                this.obtenerAlumnos()
                })
            })
        },
        eliminarAlumno(id){
            fetch('https://phs-class-api.herokuapp.com/alumno/' + id + '?numeroGrupo=4',{
            method:'DELETE',
            headers:{"Content-Type": "application/json"},})
                .then((r)=>{r.json()
                .then(()=>{this.obtenerAlumnos();
                })
            })
        },
        editarAlumno(data,id){
            fetch(' https://phs-class-api.herokuapp.com/alumno/'+id+'?numeroGrupo=4',{
            method:'PUT',
            headers:{"Content-Type": "application/json"},
            body: JSON.stringify(data)})
                .then((r)=>{r.json()
                .then(()=>{
                this.obtenerAlumnos();
        })
    })
    },
        obtenerFila(e){
            if (e.titulo=='Editar'){
                this.mostrarFormulario=true;
                this.alumnoSeleccionado=e.alumno;
                this.opcion = 2;
                }
            else if(e.titulo=='Eliminar'){ 
            this.eliminarAlumno(e.alumno._id);
            }
        },
        clickAgregar(){
            this.mostrarFormulario = true;
            this.opcion = 1;
        },
        obtenerInfoFormulario(e){
            this.mostrarFormulario = false;
            if(e.titulo == 'Aceptar' && this.opcion == 2){
                this.editarAlumno(e.alumnoSeleccionado,this.alumnoSeleccionado._id);
            }
            else if(e.titulo == 'Aceptar' && this.opcion == 1){ 
                this.crearAlumno(e.alumnoSeleccionado);
            }
            }
        },
    props:{

    },
    mounted(){
        this.obtenerAlumnos();
        }
}
</script>

<style scoped>
.alumno {
    background-color: grey;
    height: 100vh;
}
.btnagregar {
    padding: 1%;
}
</style>