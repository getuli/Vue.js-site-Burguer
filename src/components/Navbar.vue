<template>
    <nav id="nav">
        <router-link id="logo-url" to="/">
            <img id="logo" :src="logo" :alt="alt">
        </router-link> |
        <router-link to="/">Home</router-link> |
        <router-link to="/pedidos">About</router-link>
  </nav>
</template>
<script>
    export default{
        name:'Navbar',
        props:["logo", "alt"]
    }
</script>

<style scoped>
#nav{
    background-color: #222;
    border-bottom: 4px solid #111;
    display: flex;
    padding: 15px 50px;
    justify-content: flex-end;
    align-items: center;
}

#nav #logo-url{
    margin: auto;
    margin-left: 0;
}
#logo{
    width: 40px; 
    height: 40px;
}

#nav a{
    text-decoration: none;
    color:#fCBA03;
    margin: 12px;
    transition: .5s;
}
#nav a:hover{
    color:#FFF
}
</style>