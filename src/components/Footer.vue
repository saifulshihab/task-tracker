<template>
    <div>
        <p>Copyright &copy; 2021. Vue.js. <router-link to="/about">About us</router-link></p>
    </div>
</template>

<script>
export default {
    name: 'Footer'
}
</script>

<style scoped>
div{
    padding: 10px 20px;
    background: black;
    color: white;
    margin-top: 20px;
}
p{
    padding: 0;
    margin: 0;
    font-style: italic;
    font-size: 14px;
    text-align: center;
}
a{
    color: slateblue;
}
</style>