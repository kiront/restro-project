<template>
    <Header />
    <h1>Hello User, Welcome on UPdate Restaurant page</h1>
    <form action="" class="add">
        <input type="text" name="name" v-model="restaurant.name" placeholder="Name">
        <input type="text" name="address" v-model="restaurant.address" placeholder="Address">
        <input type="text" name="contact" v-model="restaurant.contact" placeholder="Contact">

        <button type="button" v-on:click="updateRestaurant">Update</button>


    </form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios';
    export default{
        name: 'UpdateRestaurant',
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
       async updateRestaurant(){
            const result = await axios.put("http://localhost:3000/restaurant/"+this.$route.params.id,{
                    name:this.restaurant.name,
                    address:this.restaurant.address,
                    contact:this.restaurant.contact
                });
                if(result.status == 200){
                    this.$router.push({name:'Home'});
                }
                console.warn(result)
            }
        },
       async mounted(){
        let user = localStorage.getItem('user-info');
        if(!user){
            this.$router.push({name:'SignUp'})
        }
        const result = await axios.get('http://localhost:3000/restaurant/'+this.$route.params.id);
        console.warn(result.data)
        this.restaurant = result.data
    }
    }
</script>