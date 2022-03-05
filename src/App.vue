<template>
  <router-view />
</template>

<script>
export default {
  name: "App",
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  padding: 0;
  margin: 0;
}

.signup input,
.login input,
.add input {
  display: block;
  width: 300px;
  height: 30px;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 10px;
  border: 1px solid skyblue;
  border-radius: 7px;
  padding: 5px;
  align-items: center;
}
.signup button,
.login button,
.add button {
  width: 307px;
  height: 35px;
  border: 2px solid skyblue;
  border-radius: 10px;
  color: white;
  background-color: skyblue;
}
.signupButton {
  background-color: skyblue;
  width: 307px;
  height: 35px;
  border: 2px solid skyblue;
  border-radius: 10px;
  color: white;
  background-color: skyblue;
  position: absolute;
  left: 504px;
}

.buttonUpdate {
  color: green;
  cursor: pointer;
  text-decoration: none;
}
.buttonDelete a {
  color: red;
  cursor: pointer;
  text-decoration: none;
}
.signup button:hover,
.add button:hover,
.login button:hover {
  color: skyblue;
  background-color: white;
}
</style>
