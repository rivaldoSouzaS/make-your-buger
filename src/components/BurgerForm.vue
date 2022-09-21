<template>
    <div>
        <p>Componente de mensagem</p>
        <div>
            <form id="burger-form">
                <div class="input-container">
                    <label for="name">customer's name</label>
                    <input type="text" id="name" name="customersName" v-model="name" placeholder="Type your name">
                </div>
                <div class="input-container">
                    <label for="bread">Choose the bread</label>
                    <select name="bread" id="bread" v-model="bread">
                        <option value="">Choose the bread</option>
                        <option value="Integral">Integral</option>
                    </select>
                </div>
                <div class="input-container">
                    <label for="meat">Choose the meat</label>
                    <select name="meat" id="meat" v-model="meat">
                        <option value="">Choose the meat</option>
                        <option value="Maminha">Maminha</option>
                    </select>
                </div>
                <div id="optionals-container" class="input-container">
                    <label id="optionals-title" for="optionals">Choose the optionals</label>
                    <div class="checkbox-container">
                        <input type="checkbox" name="optionals" v-model="optionals" value="Salami">
                        <span>Salami</span>
                    </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="optionals" v-model="optionals" value="Salami">
                        <span>Salami</span>
                    </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="optionals" v-model="optionals" value="Salami">
                        <span>Salami</span>
                    </div>
                </div>
                <div class="input-container">
                    <input type="submit" class="submit" value="Make my burger">
                </div>
            </form>
        </div>
    </div>
</template>

<script>

    export default{
        name: 'BurgerForm'
    }
</script>

<style scoped>
    #burger-form{
        max-width: 400px;
        margin: 0px auto;
    }

    .input-container{
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;
    }

    label{
        font-weight: bold;
        margin-bottom: 20px;
        padding: 5px 10px;
        border-left: 4px solid #fcba03;
    }

    input, select{
        padding: 5px 10px;
        width: 300px;
    }

    #optionals-container{
        flex-direction: row;
        flex-wrap: wrap;
    }

    #optionals-title{
        width: 100%;
    }

    .checkbox-container{
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }

    .checkbox-container span, .checkbox-container input{
        width: auto
    }

    .checkbox-container span{
        margin-left: 6px;
        font-weight: bold;
    }

    .submit{
        background-color: #222;
        color: #fcba03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 16px;
        margin: 0px auto;
        cursor: pointer;
        transition: .5s;
    }

    .submit:hover{
        background-color: transparent;
        color: #222
    }
</style>
