<template>
    <Header />
    <h1>Hello User, Welcome on Add Restaurant page</h1>

    <form action="" class="add">
        <input type="text" name="name" v-model="restaurant.name" placeholder="Name">
        <input type="text" name="address" v-model="restaurant.address" placeholder="Address">
        <input type="text" name="contact" v-model="restaurant.contact" placeholder="Contact">

        <button type="button" v-on:click="addRestaurant">Add</button>


    </form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
    export default{
        name: 'AddRestaurant',
        components: {
            Header
        },
        data(){
            return{
                restaurant:{
                    name:'',
                    address: '',
                    contact: ''
                }
            }
        },  
        methods:{
           async addRestaurant(){
                // console.warn(this.restaurant)
                const result = await axios.post("http://localhost:3000/restaurant",{
                    name:this.restaurant.name,
                    address:this.restaurant.address,
                    contact:this.restaurant.contact
                });
                if(result.status == 201){
                    this.$router.push({name:'Home'});
                }
                console.warn(result)
            }
        },
        mounted(){
        let user = localStorage.getItem('user-info');
        if(!user){
            this.$router.push({name:'SignUp'})
        }
    }
    }
</script>