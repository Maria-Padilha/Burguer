<template>
  <Navbar :logo="logo_src" :alt="alt_name" />
  <RouterView />
  <Footer_page />
</template>

<script>
  import Navbar from './components/navbar.vue';
  import Footer_page from './components/footer.vue';

  export default{
    components: {
      Navbar,
      Footer_page
    },
    data(){
      return{
        logo_src: "/img/logo.png", 
        alt_name: "Make Your Burguer"
      }
    }
  }
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Helvetica;
  }
  body{
    height: 100vh;
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
