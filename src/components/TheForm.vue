<template>

  <div id="container-form">
    
    <h2>Crie sua sala</h2>
      <form id="form" @submit="createSala">
        <div id="msg">{{Msg}}</div>
        <div id="container-input">
          <label for="nome">Nome da sala</label>
          <input type="text" alt="Nome da sala" placeholder="Nome da sala" id="nome" v-model="nome">
        </div>
        <div id="container-input">
          <label for="link">Link</label>
          <input type="text" alt="link" placeholder="Link do video" id="link" v-model="lindk">
        </div>
        <div id="Criar-assistir">
          <input type='submit' value="Criar" id="button">
          <RouterLink to="/assistir" id="a">Assistir</RouterLink>
        </div>
      </form>
  </div>
</template>

<script>    
    export default{
        name:"TheForm",
        data(){
          return{
            nome:null,
            lindk:null,

            Msg:""
          }
        },
         methods:{
          async createSala(e){
            e.preventDefault()
            const data={
              nome: this.nome,
              link:this.lindk,
            }
            // MANDAR OS DADOS DO INPUIT PARA O SERVER JSON
            const dataJson = JSON.stringify(data)
            const req = await fetch('http://localhost:3000/links',{
              method:"POST",
              headers:{"Content-Type":"application/json"},
              body:dataJson
            })
            const res = await req.json()
            // APAGAR ENTRADDA DE INPUT 
              this.nome="",
              this.lindk=""
            // MENSAGEM
              this.Msg = "Sala criada com sucesso !!"
              setTimeout(()=>this.Msg="",3000)
          }
        }
    }

</script>

<style >
  body{
    background-color: rgba(0, 0, 0, 0.952);
    color: white;
  }
  #container-form{
    
    color: white;
    height:500px;
  }
  #form {
    position:absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);

  }
  h2{
    
    text-align: center;
    margin-top:50px;
    
  }
  #msg{
    text-align: center;
    width: 400px;
    background-color: #E50914;
    font-weight: bold;
    margin-bottom: 10px;

  }
  #container-input{
    display: flex;
    flex-direction:column;
    width:400px;
  }
  #container-input input{
    height: 20px;
    margin: 10px 0 ;
  }
  #Criar-assistir {
    display: flex;
    justify-content: space-between;
    margin: 10px 20px ;
    width: 350px;
  }
  #button, #a{
    width: 100px;
    background-color:#E50914;
    padding: 10px;
    font-weight: bold;
    font-size: 1em;
    color: white;
    border-radius: 5px;
    border: #E50914;
    text-align: center;
    text-decoration: none;
  }
  #button:hover ,#a:hover{
    background-color:#af0810;
    border:black;
    box-shadow: 1px 1px 2px black;
  }
</style>