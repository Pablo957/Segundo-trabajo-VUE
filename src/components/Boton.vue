<template>
    <div id="app">
        <button class="btn" @click="enviarClick">{{titulo}}</button>
    </div>
</template>

<script> 

export default {
    name:'Boton',
    components:{

    },
    data(){
        return{
        }
    },
    methods:{
        enviarClick(){
            this.$emit('onClick',this.titulo);
        }
    },
    props:{
        titulo:String
    },
    mounted(){      
    }
}
</script>

<style>
.btn {
    background-color: #2c3e50;
    color: whitesmoke;
}
</style>
