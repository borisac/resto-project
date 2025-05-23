<template>
    <Header></Header>
    <h1>Hello, welcome to Add restaraunt page</h1>

    <form class="add">
        <input type="text" v-model="restaurant.name" placeholder="Enter name">
        <input type="text" v-model="restaurant.adress" placeholder="Enter adress">
        <input type="text" v-model="restaurant.contact" placeholder="Enter contact">
        <button v-on:click="addRestaurant">Add new restaraunt</button>
    </form>
</template>
<script>

import Header from './Header.vue'

export default {
    name:'Add',
    components:{
        Header
    },
    data(){
        return{
            restaurant:{
                name:'',
                adress:'',
                contact:'',
            }
        }
    },
     mounted(){
         let user= localStorage.getItem('user-info');
         if(!user){
            this.$router.push({name:'SignUp'});
         }
    },
    methods:{
        addRestaurant(){
            console.warn(this.restaurant);
        }
    },
}
</script>