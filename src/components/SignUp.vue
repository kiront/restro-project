<template>
    <img class="logo" src="../assets/Restaurant.png" alt="">
    <h3>Sign Up</h3>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name">
        <input type="text" v-model="email" placeholder="Enter Email">
        <input type="password" v-model="password" placeholder="Enter Password">
        <button v-on:click="signUp">Sign Up</button>

        <p>
            <router-link to="/login">Login</router-link>
        </p>
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
                localStorage.setItem("user-info", JSON.stringify(result.data))
                this.$router.push({name:'Home'})

            }
        }
    },
    mounted(){
        let user = localStorage.getItem('user-info');
        if(user){
            this.$router.push({name:'Home'})
        }
    }
}

</script>

<style>

</style>