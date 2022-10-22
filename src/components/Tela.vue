<template>
    <div  id="tela">
       {{links}}
    </div>
</template>

<script>
    export default{
        name:"Tela",
        data(){
            return{
                links:null
            }
            
        },
        methods:{
            async createTela(){
                
                const req = await fetch('http://localhost:3000/links')
                
                const res = await req.json()
                
               
                console.log(res[0].link)///caminho certo
              
            }
        },
        mounted(){
            this.createTela()
        }
        
    }
</script>

<style>

</style>