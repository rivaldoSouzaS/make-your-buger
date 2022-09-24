<template>
    <div id="burger-table">
        <div>
            <div id="burger-table-heading">
                <div class="order-id"> #</div>
                <div>Costumer</div>
                <div>Bread</div>
                <div>Meat</div>
                <div>Optionals</div>
                <div>Actions</div>

            </div>
        </div>
        <div v-for="burger in burgers" :key="burger.id" id="burger-table-rows">
            <div class="burger-table-row">
                <div class="order-number">{{burger.id}}</div>
                <div>{{burger.name}}</div>
                <div>{{burger.bread}}</div>
                <div>{{burger.meat}}</div>
                <div>
                    <ul>
                        <li v-for="(optional, index ) in burger.optionals" :key="index">
                            {{optional}}
                        </li>
                    </ul>
                </div>
                <div>
                    <select name="status" class="status">
                        <option value="">Buerger's name</option>
                    </select>
                    <button class="delete">Cancel</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Dashboard',
    data(){
        return{
            burgers: null,
            burger_id: null,
            status: []
        }
    },
    methods:{
        async getOrders(){
            const req = await fetch("http://localhost:3000/burgers")
            const data = await req.json()
            this.burgers = data;
            console.log(this.burgers)
        }
    },
    mounted(){
        this.getOrders()
    }
}
</script>

<style scoped>
    #burger-table{
        max-width: 1200px;
        margin: 0px auto;
    }

    #burger-table-heading, 
    #burger-table-rows,
    .burger-table-row{
        display: flex;
        flex-wrap: wrap;
    }

    #burger-table-heading{
        font-weight: bold;
        padding:12px;
        border-bottom: 3px solid #333;
    }

    #burger-table-heading div,
    .burger-table-row div{
        width: 19%;
    }

    .burger-table-row{
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid #333;
    }

    #burger-table-heading .order-id,
    .burger-table-row .order-number{
        width: 5%;
    }

    select{
        padding: 12px 6px;
        margin-right: 12px
    }

    .delete{
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

    .delete:hover{
        background-color: transparent;
        color: #222;
    }

</style>