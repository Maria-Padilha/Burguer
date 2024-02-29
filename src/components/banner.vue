<template>
    <section id="main-banner">
        <h1>Make Your Burguer</h1>
    </section>
</template>

<script>
    export default{
        name: "banner"
    }
</script>

<style scoped>
    #main-banner{
        background-image: url('/img/burger.jpg');
        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;
        height: 500px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }
    #main-banner h1{
        color: #fff;
        text-align: center;
        background-color: #222;
        padding: 20px 40px;
        font-size: 60px;
        font-weight: bold;
    }

    @media screen and (max-width: 1100px){
        #main-banner h1{
            font-size: 40px;
        }
    }
</style>