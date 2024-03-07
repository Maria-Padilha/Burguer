<template>
    <div class="message-container">
        <p>{{ msg }}</p>
    </div>
</template>

<script>
    export default{
        name: "Mensage",
        props: {
            msg: String
        }
    }
</script>

<style scoped>
    .message-container{
        color: #004085;
        background-color: #cce5ff;
        border: 2px solid #b8daff;
        border-radius: 5px;
        padding: 10px;
        max-width: 330px;
        margin: 0 auto;
        margin-bottom: 30px;
    }
</style>