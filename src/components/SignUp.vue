<template>
    <img class="logo" src="../assets/resto-logo.jpg"/>
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" placeholder="Enter name">
        <input type="text" placeholder="Enter email">
        <input type="text" placeholder="Enter password">
        <button>Sign Up</button>
        
    </div>
</template>

<script>

export default{
    name:'SignUp',

}
</script>

<style>
.logo{
    width: 100px;
}

.register input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid skyblue;
}

.register button{
    width: 320px;
    height: 40px;
   color: #fff;
    background: skyblue;
    border: 1px solid skyblue;
    cursor: pointer;
}
</style>