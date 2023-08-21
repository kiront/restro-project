<template>
    <Header />
    <h1>Hello User, Welcome on UPdate Restaurant page</h1>
</template>

<script>
import Header from './Header.vue'
    export default{
        name: 'UpdateRestaurant',
        components: {
            Header
        },
        mounted(){
        let user = localStorage.getItem('user-info');
        if(!user){
            this.$router.push({name:'SignUp'})
        }
    }
    }
</script>