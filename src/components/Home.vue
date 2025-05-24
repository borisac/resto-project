<template>
    <Header></Header>
     <h1>Hello, welcome to home page</h1>
     <table border="1">
        <tr>
            <td>Id</td>
            <td>Name</td>
            <td>Contact</td>
            <td>Adress</td>
            <td>Actions</td>
        </tr>
        <tr v-for="item in restaurant" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td>{{item.contact}}</td>
            <td>{{item.adress}}</td>
            <td><router-link :to="'/update/' + item.id">Update</router-link><button v-on:click="deleteRestourant(item.id)">Delete</button></td>
        </tr>
     </table>
</template>
<script>

import Header from './Header.vue'
import axios from 'axios'

export default {
    name:'Home',
    components:{
        Header
    },
    data(){
        return{
            name:'',
            restaurant:[],
    }
    },
    mounted(){

        this.loadData();
    },

    methods:{
        async deleteRestourant(id){
            let result =await axios.delete("http://localhost:3000/restaurants/"+id);
            console.warn("deleting:",id)
            console.warn(result);
             if(result.status==200){
                this.loadData();
        }
        },

        async loadData(){
              let user= localStorage.getItem('user-info');
         if(!user){
            this.$router.push({name:'SignUp'});
         }

          let result =await axios.get("http://localhost:3000/restaurants");
          console.warn(result)
          this.restaurant=result.data;
        }
    }
}
</script>

<style>
td{
    width:160px;
    height:40px;
}
</style>