<template>
    <section>
        <p>Componente de mensagem</p>
        <div>
            <form id="burger-form">
                <div class="input-container">
                    <label for="nome">Nome do cliente: </label>
                    <input type="text" id="nome" name="nome" v-model="nome" placeholder="digite seu nome">
                </div>
                <div class="input-container">
                    <label for="pao">Escolha o pão: </label>
                   <select name="pao" id="pao" v-model="pao">
                        <option value="integral">Integral</option>
                   </select>
                </div>
                <div class="input-container">
                    <label for="carne">Escolha a carne: </label>
                   <select name="carne" id="carne" v-model="carne">
                        <option value="picanha">Picanha</option>
                   </select>
                </div>

                <div id="opcionais-container" class="input-container">
                    <label id="opcionais-title" for="opcionais">Selecione os opcionais: </label>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                        <span>Salame</span>
                    </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                        <span>Salame</span>
                    </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                        <span>Salame</span>
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
    export default{
        name: "burguerForm"
    }
</script>

<style scoped>
    p{
        text-align: center;
        margin-bottom: 30px;
        display: none;
    }
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