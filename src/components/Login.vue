<template>
    <div class="login">
        <h1>Login Here</h1>
        <input type="email" placeholder="Enter email" v-model="email">
        <input type="password" placeholder="Enter password" v-model="password">
        <button v-on:click="handleLogin">Login</button>
        <p>
            <router-link to="/signup" ><a class="signupButton">Signup</a></router-link>
        </p>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name:'Login',
    data(){
        return {
            email:'',
            password:''
        }
    },
    methods:{
       async handleLogin(){
            let result = await axios.get(`http://localhost:3000/users?email=${this.email}&password=${this.password}`)
            console.log(result)
            if(result.status == 200 && result.data.length>0){
                localStorage.setItem('user-Info',JSON.stringify(result.data[0]))
                this.$router.push({name:'Home'})
            }
            
        }
        
    },
    mounted(){
        let user = localStorage.getItem('user-Info');
        if(user){
            this.$router.push({name:'Home'})
        }
    }
}
</script>


<style scoped>


</style>