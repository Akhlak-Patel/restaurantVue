<template>
    <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="/add">Add Restaurant</router-link> 
        <a v-on:click="logout" href="#">Logout</a>
    </div>
</template>
<script>
export default {
    name:'Header',
    methods:{
        logout(){
            localStorage.clear();
            this.$router.push({name:'Login'})
        }
    }
}
</script>

<style scoped>
.nav{
    background-color: #333;
    overflow: hidden    ;
    top: 0px;
}
.nav a {
    float: left;
    color: #f2f2f2;
    text-decoration: none;
    padding: 7px;
    margin: 5px;
    font-size: 20px;
    text-align: center;
}
.nav a:hover{
    background-color: #ddd;
    color: #222;
    border-radius: 8px;
}
</style>