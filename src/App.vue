
<template>
  <TheHeader/>
  <RouterView />
  <TheFooter/>
</template>
<script >
  import TheHeader from './components/TheHeader.vue'
  import TheFooter from './components/TheFooter.vue';
  export default{
    name:"App",
    components:{ TheHeader, TheFooter },
    data(){
      return{

      }
    }
  }
</script>
  

<style >
  @import url('https://fonts.googleapis.com/css2?family=Playfair+Display&display=swap');
   body{
        margin: 0;
        padding: 0;
    }
</style>
