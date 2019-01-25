<template>
    <div>
        <h3>Informacion del usuario</h3>
        <div>
            <p><strong>Nombre: </strong>{{nombre}}</p>
            <p><strong>Correo Electronico: </strong>{{email}}</p>
        </div>
        <button class="btn btn-primary" @click="volver">Volver</button>
    </div>
</template>
<script type="text/javascript">
    export default{
        data(){
            return {
                nombre: '',
                email: ''
            }
        },
        methods:{
            volver(){
                this.$router.push({name: 'usuarios'});
            }
        },
        created(){
            let id = this.$route.params.id;
            this.$http.get('https://jsonplaceholder.typicode.com/users/' + id)
                           .then(respuesta =>{
                                this.nombre = respuesta.body.name;
                                this.email = respuesta.body.email
                           })
        }
    }
</script>