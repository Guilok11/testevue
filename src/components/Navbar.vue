<template>
  <div id="nav">
    <RouterLink to="/" id="logo_url">
        <img :src="logo" :alt="alt" id="logo">
    </RouterLink>
    <router-link to="/">Home</router-link>
    <router-link to="/pedidos">Pedidos</router-link>
  </div>

</template>

<script>
export default{
    name: "Navbar",
    props: ["logo", "alt"]

}

</script>

<style scoped>
    #nav {
        background-color: #111;
        border-bottom: 4px solid #111;
        padding: 15px 50px;
        display: flex;
        justify-content: flex-end;
        align-items: center;
    }

    #nav #logo_url {
        margin: auto;
        margin-left: 0;
    }

    #logo {
        width: 40px;
        height: 40px;
    }

    #nav a {
        color: #fcba03;
        text-decoration: none;
        margin: 12px;
        transition: .5s;

    }

    #nav a:hover{
        color: #FFF;
    }

</style>