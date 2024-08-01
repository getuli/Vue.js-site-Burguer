<template>
  <Navbar  :logo="logo_src" :alt="alt"/>
  <router-view/>
  <Footer/>
</template>
<script>
import Navbar from './components/Navbar.vue';
import Footer from './components/Footer.vue';



export default{
  name:'App',
  data(){
  return{
        logo_src:"/img/logo.png ",
        alt:'make Your Burguer'
  }


  
},
  components:{
  Navbar,
  Footer
}

}


</script>
<style>
*{
  font-family:Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.main-container{
  margin: 50px;
  min-height: 250px;
}
h1{
  font-size: 42px;
  align-items: center;
  margin-bottom: 30px;
  color: #222;
}

#footer{
  height: 200px;
  background-color:#222 ;
  border-top: 4px solid #111;
  color: #fCBA03;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
</style>
