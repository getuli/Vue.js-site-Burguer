<template>
   <div class="main-banner">
    <h1>make your Burger</h1>
   </div>
</template>
<script >
   
    export default{
        name:'Banner',
    }
</script>

<style scoped>
.main-banner{
    background-image: url('/public/img/burger.jpg');
    background-position: 0 -250px;
    height: 500px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    background-size: cover;

}
.main-banner h1{
    color: #EEE;
    background-color:#222 ;
    text-align: center;
    font-size: 60px;
    padding: 20px 40px;
}
</style>