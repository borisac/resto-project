<template>
    <Header></Header>
     <h1>Hello, welcome to Update restaraunt page</h1>
     <form class="add">
        <input type="text" v-model="restaurant.name" placeholder="Enter name">
        <input type="text" v-model="restaurant.adress" placeholder="Enter adress">
        <input type="text" v-model="restaurant.contact" placeholder="Enter contact">
        <button v-on:click="updateRestaurant">Update new restaraunt</button>
    </form>
</template>
<script>

import Header from './Header.vue'
import axios from 'axios'

export default {
    name:'Update',
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

     async mounted(){
         let user= localStorage.getItem('user-info');
         if(!user){
            this.$router.push({name:'SignUp'});
         }
         const result = await axios.get("http://localhost:3000/restaurants?id="+this.$route.params.id);
     
         console.warn(result);
          if (result.data && result.data.length > 0) {
        this.restaurant = result.data[0]; 
    } else {
        console.warn("Restaurant not found!");
    }
    },

    methods:{
       async updateRestaurant(){ 
            console.warn(this.restaurant);
        const result = await axios.put("http://localhost:3000/restaurants/"+this.$route.params.id,{
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