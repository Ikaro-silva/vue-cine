<template>
    <!-- TELA PARA EXIBIR O VIDEO -->
    <div id="mainTela">
        <h2>Se Divirta ...</h2>
        <div  id="tela">
        
        </div>
    </div>
    <!-- /TELA PARA EXIBIR O VIDEO -->
    <!-- Lista DE SALAS  -->
    <table id="mainTable">
        <thead>
            <tr>
                <th>N°</th>
                <th>Sala</th>
            </tr>
        </thead>
        <tbody >
            <tr v-for="sala in salas" :key="sala.id">
                <td>{{sala.id}}</td>
                <td>{{sala.nome}}</td>
                <button @click="deleteSala(sala.id)">Delete</button>
                
                <button @click="createTela(sala.id)">
                    Assistir
                </button>
            </tr>
        </tbody>
    </table>
    <!--/ Lista DE SALAS  -->
</template>

<script>
    export default{
        name:'ListaSala',
        data(){
            return{
                salas:null,
                links:null
            }
        },
        methods:{
            // RESPONSAVEL POR TRAZER DADOS DO JSON PARA  LISTA DE SALA
            async createLista(){
                const req = await fetch('http://localhost:3000/links')
                const res = await req.json()
                this.salas= res
                  
            },
            // RESPONSAVEL POR DELETAR SALA DO JSON

            async deleteSala(id){
                const req = await fetch (`http://localhost:3000/links/${id}`,{
                    method:'DELETE'
                });
                
                this.createLista()
            },
            // RESPOSAVEL POR TRAZER O VIDEO  VIA ID PARA SER EXIBIDO 
            async createTela(id){
                const req = await fetch(`http://localhost:3000/links/${id}`)
                const res = await req.json()
                const video= res.link
                
                const containeLink = document.getElementById("tela")
                containeLink.innerHTML=video
               
            }
        },
        mounted(){
            // CHAMA SEMPRE QUE A PAGINA É CARREGADA A LISTA DE SALA 
            this.createLista()
        }
    }
</script>

<style scoped>
    #mainTable{
        color: white;
        margin: auto;
        
        border-collapse: collapse;

        
    }
    #mainTable tr{
        border: 1px solid white;
        text-align: center;
       
        
    }
    #mainTable th,
    #mainTable td{
        
        padding: 10px;
    }
    button, a{
    vertical-align:middle;
    font-family: Arial, Helvetica, sans-serif;
    background-color:#E50914;
    padding:5px;
    font-weight: bold;
    color: white;
    border-radius: 5px;
    border: #E50914;
    text-align: center;
    text-decoration: none;
    margin: 10px;
  }
  button:hover ,a:hover{
    background-color:#af0810;
    border:black;
    box-shadow: 1px 1px 2px black;
  }
  /* Tela */
  #tela{
    margin:50px;
    text-align: center;
  }
  #mainTela h2{
    text-align: center;
    color:white

  }
</style>