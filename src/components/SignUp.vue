<template>
    <img class="logo" src="../assets/Restaurant.png" alt="">
    <h3>Sign Up</h3>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name">
        <input type="text" v-model="email" placeholder="Enter Email">
        <input type="password" v-model="password" placeholder="Enter Password">
        <button v-on:click="signUp">Sign Up</button>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'SignUp',
    data() {
        return {
            name: '',
            email: '',
            password: '',
        }
    },
    methods:{
       async signUp(){
            console.warn(this.name, this.email, this.password)
            let result = await axios.post("http://localhost:3000/users",{
                email:this.email,
                name:this.name,
                password:this.password
            });
            console.warn(result);
            if(result.status == 201){
                alert("signup done")
            }
            localStorage.setItem("user-info", JSON.stringify(result.data))
        }
    }
}

</script>

<style>
.logo {
    width: 100px;
}

.register input {
    width: 300px;
    height: 40px;
    padding-left: 20px;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid skyblue;
}

.register button {
    width: 320px;
    height: 40px;
    border: 1px solid skyblue;
    background-color: skyblue;
    cursor: pointer
}
</style>