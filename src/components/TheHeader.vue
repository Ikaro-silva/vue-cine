<template>
    <div id="container-main">
        <a href="/">
            <h1>Cine-rural</h1>
        </a>
        <nav>
          <RouterLink to="/">Home</RouterLink>
          
        </nav>
    </div>
</template>
<script>
    export default{
        name:"TheHeader"
    }
</script>
<style scoped>
    
   
    #container-main{
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #E50914;
        height: 70px;
        padding:0 50px 0 30px;
    }
    #container-main h1{
        color: white;
        font-family: 'Playfair Display', serif
    }
    #container-main a{
        color:white;
        text-decoration: none;
        padding-left:15px;
        font-weight: bold;
        cursor:pointer
    }
    #container-main a:hover{
        transition: 0.2s;
        color:rgb(255, 101, 101);
        text-shadow: 1px 1px 2px black;
    }
</style>