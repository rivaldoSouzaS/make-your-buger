<template>
    <div>
        <!--componente de mensagem-->
        <Message :msg="msg" v-show="msg"/>
        <!--componente de mensagem-->
        <div>
            <form id="burger-form" @submit="createBurguer">
                <div class="input-container">
                    <label for="name">customer's name</label>
                    <input type="text" id="name" name="customersName" v-model="name" placeholder="Type your name">
                </div>
                <div class="input-container">
                    <label for="bread">Choose the bread</label>
                    <select name="bread" id="bread" v-model="bread">
                        <option value="">Choose the bread</option>
                        <option v-for="bread in breads" :key="bread.id" :value="bread.tipo">{{bread.tipo}}</option>
                    </select>
                </div>
                <div class="input-container">
                    <label for="meat">Choose the meat</label>
                    <select name="meat" id="meat" v-model="meat">
                        <option value="">Choose the meat</option>
                        <option v-for="meat in meats" :key="meat.id" :value="meat.tipo">{{meat.tipo}}</option>>
                    </select>
                </div>
                <div id="optionals-container" class="input-container">
                    <label id="optionals-title" for="optionals">Choose the optionals</label>
                    <div v-for = "optional in optionalsData" :key="optional.id" class="checkbox-container">
                        <input type="checkbox" name="optionals" v-model="optionals" :value="optional.tipo">
                        <span>{{optional.tipo}}</span>
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
    import Message from './Message.vue'

    export default{
    name: "BurgerForm",
    data() {
        return {
            breads: null,
            meats: null,
            optionalsData: null,
            name: null,
            bread: null,
            meat: null,
            optionals: [],
            msg: null
        };
    },
    methods: {
        async getIngredients() {
            const req = await fetch("http://localhost:3000/ingredientes");
            const data = await req.json();
            this.breads = data.paes;
            this.meats = data.carnes;
            this.optionalsData = data.opcionais;
        },
        async createBurguer(event) {
            event.preventDefault();
            const data = {
                name: this.name,
                meat: this.meat,
                bread: this.bread,
                optionals: Array.from(this.optionals),
                status: "Solicitado"
            };
            const dataJson = JSON.stringify(data);
            //console.log(dataJson);
            const req = await fetch("http://localhost:3000/burgers", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: dataJson
            });

            const res = await req.json();

            this.msg = `Order n° ${res.id} placed successfully`
            setTimeout(()=>this.msg = "", 3000)

            this.name = "";
            this.meat = "";
            this.bread = "";
            this.optionals = "";
        }
    },
    mounted() {
        this.getIngredients();
    },
    components: { 
        Message 
    }
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
