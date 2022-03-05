<template>
<div>
    <Header/>
    <h1>Welcome to the Add Restaurant page</h1>
    <div class="add">
        <input type="text" name="name" v-model="restaurant.name" placeholder="Enter Restuarant Name" >
        <input type="text" name="address" v-model="restaurant.address" placeholder="Enter Restaurant Address">
        <input type="text" name="contact" v-model="restaurant.contact" placeholder="Enter Contact Number">
        <button v-on:click="handleAdd" type="submit">Add</button>
    </div>
    
</div>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios'
export default {
    name:'Add',
    components:{Header},
    data(){
        return {
            restaurant:{
                name:'',
                address:'',
                contact:''
            }
        }
    },
    methods:{
        async handleAdd(){
            const result = await axios.post('http://localhost:3000/restaurant',{
                name:this.restaurant.name,
                address:this.restaurant.address,
                contact:this.restaurant.contact
            })
                console.log(result.status)
            if(result.status == 201){
                this.$router.push({name:'Home'})
            }
        }
    },
    mounted(){
        let user = localStorage.getItem('user-Info');
        if(!user){
            this.$router.push({name:'login'})
        }
    }
}
</script>