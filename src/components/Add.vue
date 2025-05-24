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
import axios from 'axios'

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
       async addRestaurant(){ 
            console.warn(this.restaurant);
        const result = await axios.post("http://localhost:3000/restaurants",{
            name: this.restaurant.name,
            contact: this.restaurant.contact,
            adress: this.restaurant.adress,
        });
         console.warn("result" , result);
        if(result.status==201){
                this.$router.push({name:'Home'});
        }
                   

        }
    },
}
</script>