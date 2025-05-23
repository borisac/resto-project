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
export default{
    name:'Login'
}
</script>