<template>
    <img class="logo" src="../assets/Restaurant.png" alt="">
    <h3>Sign Up</h3>
    <div class="register">
        <input type="text" placeholder="Enter Name">
        <input type="text" placeholder="Enter Email">
        <input type="password" placeholder="Enter Password">
        <button>Sign Up</button>
    </div>
</template>

<script>
export default{
    name: 'SignUp'
}
</script>

<style>
.logo{
    width: 100px;
}
.register input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid skyblue;
}
.register button{
    width: 320px;
    height: 40px;
    border: 1px solid skyblue;
    background-color: skyblue;
    cursor:pointer
}
</style>