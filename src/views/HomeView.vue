<template>
  <banner />
  <main class="main-container">
    <h2>Monte o seu burguer:</h2>
    <burgerForm />
    
  </main>
</template>

<script>
  import banner from '@/components/banner.vue';
  import burgerForm from '@/components/burgerForm.vue';

  export default{
    components:{
      banner,
      burgerForm
    }
  }
</script>