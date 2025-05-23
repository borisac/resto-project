<template>
    <img class="logo" src="../assets/resto-logo.jpg"/>
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter name">
        <input type="text" v-model="email" placeholder="Enter email">
        <input type="password" v-model="password" placeholder="Enter password">
        <button v-on:click="signUp">Sign Up</button>
        <p> <router-link to="login">
            Login page
        </router-link></p>
    </div>
</template>

<script> 

import axios from 'axios'

export default{
    
    name:'SignUp',

    data(){
        return{
            name:'',
            password:'',
            email:''
        }
    },
    methods:{
        async signUp(){
            let result = await axios.post("http://localhost:3000/users",{
                    name:this.name,
                    password:this.password,
                    email:this.email
            });
            console.warn("TEST TEXT FOR SIGN UP", this.name,this.email,this.password);
            console.warn("result promenljiva: ", result);

            if(result.status==201){
                alert("sign up done");
                localStorage.setItem("user-info", JSON.stringify(result.data));
                this.$router.push({name:'Home'});
            }
        }
    },
    mounted(){
         let user= localStorage.getItem('user-info');
         if(user){
            this.$router.push({name:'Home'});
         }
    },

}
</script>

<style>
</style>