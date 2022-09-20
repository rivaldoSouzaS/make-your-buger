<template>
  <NavBar :logo = "logo_src" :alt="nomeDoProjeto"/>
  <router-view/>
  <Footer/>
</template>

<script>
  import NavBar from "./components/NavBar.vue"
  import Footer from "./components/Footer.vue"
  export default {
    components:{
      NavBar,
      Footer
    },
    data(){
      return{
        logo_src:"/img/logo.png",
        nomeDoProjeto: "make your burger"
      }

    }
  }
</script>

<style>
 *{
  font-family: Arial, Helvetica, sans-serif;
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
 }

 .main-container{
  margin: 50px;
  min-height: 250px;
 }

 h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
 }
</style>
