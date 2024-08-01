<template>
  <Banner/>
  <div class="main-container">
    <h1>Faça seus pedidos:</h1>
    <Burguerform/>
  </div>

</template>

<script>
import Banner from '../components/Banner.vue';
import Burguerform from '../components/Burguerform';


export default{
  name:'Home',

  components:{
    Banner,
    Burguerform
  }
}

</script>
