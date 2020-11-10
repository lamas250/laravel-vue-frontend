<template>
    <div class="navbar">
        <h3 class="logo">Logo</h3>
        <a href="" @click.prevent="logout" class="logout">Sair <i class="fa fa-sign-out-alt"></i></a>
    </div>
</template>

<script>
export default {
    name: 'NavbarComponent',
    methods: {
        logout(){
            this.$router.push({name: 'login'});
        }
    }
}
</script>

<style lang="scss">
.navbar {
    background-color: #203d85dc;

    .logo {
        color: #fff
    }

    .logout {
        text-decoration: none;
        color: #fff
    }
}




</style>