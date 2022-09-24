<template>
  <div class="main-container">
    <h1>Manage orders</h1>
    <Dashboard />
  </div>
</template>

<script>
  import Dashboard from '../components/Dashboard.vue'

export default {
  name: "Pedidos",
  data(){
    return{

    }
  },
  components:{
    Dashboard
  }
}
</script>

<style scoped>

</style>
