<template>
  <div class="main-container">
    <Banner/>
    <h1>Make your burger</h1>
  </div>
</template>

<script>
  
import Banner from '../components/Banner.vue';
  export default{
    name: 'HomeView',
    components:{
      Banner
    }
  }
</script>
