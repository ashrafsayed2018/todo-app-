<template>
    <div class="header">
        <h1><a href="">Todo List</a></h1>
        <div id="nav">
            <router-link to="/">home</router-link>
            <router-link to="about">about</router-link>
        </div>
    </div>
</template>
<script>
export default {
    name : "Header"
}
</script>
<style scoped>
.header {
    background-color: #333;
    color: #fff;
    text-align: center;
    padding: 10px;
}
.header a {
    text-decoration: none;
    color: currentColor;
    padding: 5px;
}
</style>