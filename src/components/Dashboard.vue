<template>
    <div id="burger-table">
        <div>
            <div id="burguer-table-heading">
                <div class="order-id"> #</div>
                <div>Costumer</div>
                <div>Bread</div>
                <div>Meat</div>
                <div>Optionals</div>
                <div>Actions</div>

            </div>
        </div>
        <div id="burguer-table-rows">
            <div class="burguer-table-row">
                <div class="order-number">1</div>
                <div>Rivaldo</div>
                <div>Italian Bread</div>
                <div>Picanha</div>
                <div>
                    <ul>
                        <li>Tomatoes</li>
                        <li>Salame</li>
                        <li>Potatoes</li>
                    </ul>
                </div>
                <div>
                    <select name="status" class="status">
                        <option value="">Buerger's name</option>
                    </select>
                    <button class="delete">Cancel</button>
                </div>
            </div>
            <div class="burguer-table-row">
                <div class="order-number">1</div>
                <div>Rivaldo</div>
                <div>Italian Bread</div>
                <div>Picanha</div>
                <div>
                    <ul>
                        <li>Tomatoes</li>
                        <li>Salame</li>
                        <li>Potatoes</li>
                    </ul>
                </div>
                <div>
                    <select name="status" class="status">
                        <option value="">Buerger's name</option>
                    </select>
                    <button class="delete">Cancel</button>
                </div>
            </div>
            <div class="burguer-table-row">
                <div class="order-number">1</div>
                <div>Rivaldo</div>
                <div>Italian Bread</div>
                <div>Picanha</div>
                <div>
                    <ul>
                        <li>Tomatoes</li>
                        <li>Salame</li>
                        <li>Potatoes</li>
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

        }
    }
}
</script>

<style scoped>
    #burger-table{
        max-width: 1200px;
        margin: 0px auto;
    }

    #burguer-table-heading, 
    #burguer-table-rows,
    .burguer-table-row{
        display: flex;
        flex-wrap: wrap;
    }

    #burguer-table-heading{
        font-weight: bold;
        padding:12px;
        border-bottom: 3px solid #333;
    }

    #burguer-table-heading div,
    .burguer-table-row div{
        width: 19%;
    }

    .burguer-table-row{
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid #333;
    }

    #burguer-table-heading .order-id,
    .burguer-table-row .order-number{
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