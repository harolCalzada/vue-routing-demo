<template>
    <div>
        <p>Lista de usuarios</p>
        <ul class="list-group">
            <router-link tag="li" :to="{name: 'infoUsuario', params: {id: usuario.id}}" class="list-group-item" v-for="usuario in usuarios">{{usuario.name}}</router-link >

        </ul>
        <router-view></router-view>
    </div>
</template>
<script type="text/javascript">
    export  default{
        data(){
            return {
                id: this.$route.params.id,
                usuarios : {}
            }
        },
        created(){
            this.$http.get('https://jsonplaceholder.typicode.com/users')
                           .then(respuesta => {
                                this.usuarios = respuesta.body
                           })

        }
    }
</script>