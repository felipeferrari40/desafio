<template>
    <nav id="nav">
        <router-link to="/">Cadastrar</router-link>
        <router-link to="/about">Registro</router-link>
    </nav>
</template>

<script>

export default {
    name: 'Header'
}
</script>

<style scoped>

#nav{
    background-color: #EEE;
    border-bottom: 4px solid #FFF;
    padding: 15px 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
}

#nav a{
    color: #006128;
    text-decoration: none;
    margin: 12px;
    transition: .5s;
}

#nav a:hover{
    color: #000;
}

</style>