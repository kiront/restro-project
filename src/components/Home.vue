<template>
    <h1>Hello User, Welcome on Home page</h1>
</template>

<script>
    export default{
        name: 'HomeComponent',
        mounted(){
        let user = localStorage.getItem('user-info');
        if(!user){
            this.$router.push({name:'SignUp'})
        }
    }
    }
</script>