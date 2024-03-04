<template>
  <main class="main-container">
    <h1>Gerenciar Pedidos</h1>
    <dashboard />
  </main>
</template>

<script>
  import dashboard from '@/components/dashboard.vue';

  export default{
    name: "pedidos",
    components: {
      dashboard
    }
  }
</script>