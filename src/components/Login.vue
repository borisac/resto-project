<template>
    <img class="logo" src="../assets/resto-logo.jpg"/>
    <h1>Login</h1>
    <div class="login">
        <input type="text" v-model="email" placeholder="Enter email">
        <input type="password" v-model="password" placeholder="Enter password">
        <button v-on:click="login">Login</button>
        <p> <router-link to="sign-up">
            Sign up page
        </router-link></p>
    </div>
</template>
<script>

import axios from 'axios'

export default{
    name:'Login',

    data(){
        return{
            email:'',
            password:''
        }
    },
    
    mounted(){
         let user= localStorage.getItem('user-info');
         if(user){
            this.$router.push({name:'Home'});
         }
    },
    
    methods:{

        async login(){
            let result = await  axios.get(`http://localhost:3000/users?email=${this.email}&password=${this.password}`)
            console.log(result);

                 if(result.status==200 && result.data.length>0){
                alert("sign up done");
                localStorage.setItem("user-info", JSON.stringify(result.data[0]));
                this.$router.push({name:'Home'});
            }
        }
    }
}
</script>