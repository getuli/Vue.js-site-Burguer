<template>
    <div>
        <p>Mensagem</p>
        <div>
            <form id="burger-form" @submit="createburger">
                <div class="input-container">
                    <label for="nome">Nome do cliente</label>
                    <input type="text" name="nome" class="nome" v-model="nome" placeholder="Digite o seu nome ...">
                </div>
                <div id="opcionais-container" class="input-container">
                    <label for="pao">Escolha o pão</label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="">Selecione o seu pão</option>
                        <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
                            {{ pao.tipo }}
                        </option>
                    
                    </select>
                </div>
                <div class="input-container">
                    <label for="pao">Escolha a carne</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value="">Selecione a carne</option>
                        <option value="carne">Carne do seu burger</option>
                        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
                            {{ carne.tipo }}
                        </option>
       
                    </select>
                </div>
                <div class="input-container">
                    <label id="opcionais-title" for="opcionais">Selecione os opcionais</label>
                    <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">

                        <input type="checkbox" name="opcionais" :value="opcional" v-model="opcionais">
                        <span>{{ opcional.tipo }}</span>
                    </div>
                </div>
                <div>
                    <input type="submit" name="submit-btn" class="submit-btn" value="criar meu burger">
                </div>
            
            
            </form>
        </div>
       
    </div>
</template>

<script>
    export default {
        name:'Burguerform',
        data(){
            return{
                paes:null,
                carnes:null,
                opcionaisdata:null,
                nome:null,
                pao:null,
                status:'solicitado',
                msg:null
            }
        },
        methods:{
            async getIngredientes(){
                const req = await fetch('http://localhost:3000/ingredientes');
                const data = await req.json();  
                
                console.log(data)

                this.paes = data.paes
                this.carnes = data.carnes
                this.opcionaisdata = data.opcionais
          
            },
            async createburger(e){
                e.prevent.default();
           
                const data = {
                    nome : this.nome,
                    carne : this.carne,
                    pao : this.pao,
                    opcionais : Array.from(this.opcionais),                    status :"solicitado"
                }
                const dataJson = JSON.stringify(data)

                const req = await fetch("http://localhost:3000/burgers",{
                    methods:'POST',
                    headers: {"Content-Type": "aplicaion-json"},
                    body: dataJson
                })
            }
        },
        mounted(){
            this.getIngredientes()
        }
  }
</script>

<style scoped>

#burger-form{
    max-width: 400px;
    margin: 0 auto;
}

.input-container{
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}

label{
    color: #222;
    font-weight: bold;
    margin-bottom: 15px;
    padding: 5px 10px;
    border-left: 4px solid #FCBA03;
}

input, select{
    padding: 5px 10px;
    width: 300px;
}
#opcionais-container{
    flex-direction: row;
    flex-wrap: wrap;

}
#opcionais-title{
    width: 100%;
}
.checkbox-container{
    display: flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 20px;
    -left:10px ;
}

.checkbox-container span,
.checkbox-container input{
    width: auto;
}
.checkbox-container{
    margin-left: 6px;
    font-weight: bold;
}

.submit-btn{
    background-color: #222;
    color: #FCBA03;
    padding: 10px;
    border: 2px solid black;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;

}
.submit-btn:hover{
    background-color: transparent;
    color: #222;
}
</style>