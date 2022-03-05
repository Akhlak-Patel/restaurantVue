<template>
  <div>
    <Header />
    <h1>Hello {{ name }} , Welcome to the home page</h1>
    <table border="1" class="table">
      <tr>
        <th>Id</th>
        <th>Name</th>
        <th>Address</th>
        <th>Contact</th>
        <th colspan="2">Operations</th>
      </tr>
      <tr v-for="resto in allResto" :key="resto.id">
        <td>{{resto.id}}</td>
        <td>{{resto.name}}</td>
        <td>{{resto.address}}</td>
        <td>{{resto.contact}}</td>
        <td ><router-link :to="'/update/'+resto.id" class="buttonUpdate">Update</router-link></td>
        <td class="buttonDelete" v-on:click="deleteRestaurant(resto.id)"><a>Delete</a></td>
      </tr>
    </table>
  </div>
</template>
<script>
import Header from "./Header.vue";
import axios from 'axios'
export default {
  name: "Home",
  components: { Header },
  data() {
    return {
      name: "",
      allResto:[]
    };
  },
  methods:{
    async deleteRestaurant(id){
      let result = await axios.delete('http://localhost:3000/restaurant/'+id);
      if(result.status == 200){
        this.loadData()
      }
    },
   async loadData() {
     let user = localStorage.getItem("user-Info");
    this.name = JSON.parse(user).name
    if (!user) {
      this.$router.push({ name: "Signup" });
    }
    let result = await axios.get('http://localhost:3000/restaurant');
    this.allResto = result.data

   }
  },
 async mounted() {
  this.loadData();    
  },
};
</script>

<style scoped>
.table{
    display: inline-block;
}
td,th{
    padding: 10px;
    border: 2px solid black;
    color: #fff;
    background-color: #333;
}
</style>