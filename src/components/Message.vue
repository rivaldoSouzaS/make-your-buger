<template>
    <div class="message-container">
        <p>{{msg}}</p>
    </div>
</template>

<script>
export default {
    name: 'Message',
    props:{
        msg: String
    },
    data(){
        return{

        }
    }
}
</script>

<style scoped>
    .message-container{
        color:#004085;
        background-color: #cce5ff;
        border: 2px solid #b8daff;
        border-radius: 5px;
        padding: 10px;
        max-width : 300px;
        margin: 30px auto;
        transition: .5s; /*<!--essa propriedade nao esta funcionando-->*/
    }
</style>