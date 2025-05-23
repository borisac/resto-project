<template>
    <div class="nav">
        <a href="#">Home</a>
        <router-link to="/add">Add restaraunt</router-link>
        <router-link to="/update">Update restaraunt</router-link>
        <a href="#">Delete restaraunt</a>
        <a href="#" v-on:click="logout">Logout</a>
    </div>
</template>
<script>
export default{
    name:'Header',

    methods:{
        logout(){
            console.warn("logout")
            localStorage.clear();
            this.$router.push({name:'Login'})
        },
        
    }
}
</script>
<style>
.nav{
    background-color: #333;
    overflow: hidden;
}

.nav a{
    float: left;
    color: #f2f2f2f2;
    padding:14px 16px;
    margin: 5px;
    text-align: center;
    font-size: 17px;
    text-decoration: none;

}

.nav a:hover{
    background: #ddd;
    color:#333
}
</style>