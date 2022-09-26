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
                    <select @change="updateBurger($event, burger.id)" name="status" class="status">
                        <option v-for="statu in status" :key="statu.id" :value="statu.tipo" :selected="burger.status == statu.tipo">
                            {{statu.tipo}}
                        </option>
                    </select>
                    <button @click="deleteBurher(burger.id)" class="delete">Cancel</button>
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
        },

        async getStatus(){
            const req = await fetch("http://localhost:3000/status")
            const data = await req.json()
            this.status = data;

            console.log(this.status)
        },

        async deleteBurher(id){
            const req = await fetch(`http://localhost:3000/burgers/${id}`,{
                method: "DELETE"
            })
            const res = await req.json()
            //msg
            this.getOrders()
        },
        async updateBurger(event, id){
            const option = event.target.value

            const dataJson = JSON.stringify({status: option});
            const req = await fetch(`http://localhost:3000/burgers/${id}`, {
                method: "PATCH",
                headers: { "Content-Type": "application/json" },
                body: dataJson
            });
            const res = await req.json()
        }
    },
    mounted(){
        this.getOrders(),
        this.getStatus()
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