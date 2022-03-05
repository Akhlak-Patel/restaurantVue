<template>
  <div class="signup">
    <h1>Signup here</h1>
    <input type="text" placeholder="Enter name" v-model="name" />
    <input type="email" placeholder="Enter Email" v-model="email" />
    <input type="number" placeholder="Enter age" v-model="age" />
    <input type="password" placeholder="Enter password" v-model="password" />
    <button v-on:click="signUp">Signup</button>
    <p>
      <router-link to='/login'><a class="signupButton">Login</a></router-link>
      </p>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: "Signup",
  data() {
    return {
      name: "",
      email: "",
      age: "",
      password: "",
    };
  },
  methods: {
    async signUp() {
      // console.log('singup',this.name,this.email,this.age,this.password)
      // let result =await axios.post("http://localhost:3000/users",{
      //   name:this.name,
      //   email:this.email,
      //   age:this.age,
      //   password:this.password
      // })
      axios.post("http://localhost:3000/users",{
        name:this.name,
        email:this.email,
        age:this.age,
        password:this.password
      }).then((res)=>{
        console.log(res)
        if(res.status === 201){
          localStorage.setItem('user-Info',JSON.stringify(res))
          this.$router.push({name:'Home'})
        }
      })
    },
  },
  mounted(){
    let user = localStorage.getItem('user-Info');
    if(user)
    {
      this.$router.push({name:'Home'})
    }
    
  }
};
</script>

<style scoped>


</style>