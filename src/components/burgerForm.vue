<template>
    <section>
        <mensage :msg="msg" v-show="msg"/>
        <div>
            <form id="burger-form" @submit="createBurger">
                <div class="input-container">
                    <label for="nome">Nome do cliente: </label>
                    <input type="text" id="nome" name="nome" v-model="nome" placeholder="digite seu nome">
                </div>
                <div class="input-container">
                    <label for="pao">Escolha o pão: </label>
                   <select name="pao" id="pao" v-model="pao">
                        <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
                            {{ pao.tipo }}
                        </option>
                   </select>
                </div>
                <div class="input-container">
                    <label for="carne">Escolha a carne: </label>
                   <select name="carne" id="carne" v-model="carne">
                        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
                            {{ carne.tipo }}
                        </option>
                   </select>
                </div>

                <div id="opcionais-container" class="input-container">
                    <label id="opcionais-title" for="opcionais">Selecione os opcionais: </label>
                    <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                        <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                        <span>{{ opcional.tipo }}</span>
                    </div>
                </div>
                
                <div class="input-container">
                    <input type="submit" class="submit-btn" value="Criar o Burguer">
                </div>
            </form> 
        </div>
    </section>
</template>

<script>
    import mensage from './mensage.vue';

    export default{
        name: "burguerForm",
        // pegando todas as variáveis e declarando como nulo
        data(){
            return{
                id: 1,
                paes: null,
                carnes: null,
                opcionaisdata: null,
                nome: null,
                pao: null,
                carne: null,
                opcionais: [],
                msg: null
            }
        },
        components: {
            mensage
        },
        methods: {
            // pegando os igredientes já cadastrados no banco
            async getIngredientes(){
                // manda uma busca para a porta
                const req = await fetch("http://localhost:3000/ingredientes");
                const data =  await req.json();
                
                // as variaveis criadas recebem os valores do banco
                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisdata = data.opcionais;
            },
            // mandando novo pedido para o banco
            async createBurger(e){
                e.preventDefault();

                // cria um objeto com os valores que foram inseridos no input 
                const data = {
                    nome: this.nome,
                    carne: this.carne,
                    pao: this.pao,
                    opcionais: Array.from(this.opcionais),
                    status: "Solicitado"
                }

                // transforma esse objeto num campo de texto
                const dataJson = JSON.stringify(data);

                // prepara o caminho e o método
                const req = await fetch("http://localhost:3000/burguers",{
                    method: "POST",
                    headers: {"Content-Type": "application/json"},
                    body: dataJson
                });

                // encaminha para a porta dos pedidos
                const res = await req.json();

                // mensagem de pedido realizado
                this.msg = "Pedido realizado com sucesso!"

                // limpar mensagem
                setTimeout(() => this.msg = "",3000);

                // LIMPAR OS CAMPOS
                this.nome = "";
                this.carne = "";
                this.pao = "";
                this.opcionais = "";
            }
        },
        mounted(){
            this.getIngredientes();
        }
    }
</script>

<style scoped>
    #burger-form{
        max-width: 330px;
        margin: 0 auto;
    }
    .input-container{
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }
    .input-container input,
    .input-container select{
        padding: 10px;
        border: 1px solid #222;
        border-radius: 2px;
    }
    .input-container input:focus{
        outline: none;
    }
    option{
        border: none;
    }
    label{
        font-weight: bold;
        margin-bottom: 10px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid #fcba03;
        text-align: left;
    }
    input, select{
        padding: 5px 10px;
        width: 300px;
    }
    #opcionais-container{
        flex-direction: row;
        flex-wrap: wrap;
    }
    .checkbox-container{
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }
    .checkbox-container span,
    .checkbox-container input{
        width: auto;
    }
    .checkbox-container span{
        margin-left: 6px;
        font-weight: bold;
    }
    .submit-btn{
        background-color: #222;
        color: #fcba03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }
    .submit-btn:hover{
        background-color: transparent;
        color: #222;
    }
</style>