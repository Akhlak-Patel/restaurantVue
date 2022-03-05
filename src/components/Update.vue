<template>
  <div>
    <Header />
    <h1>Welcome to the Update Restaurant page</h1>
    <div class="add">
      <input
        type="text"
        name="name"
        v-model="restaurant.name"
        placeholder="Enter Restuarant Name"
      />
      <input
        type="text"
        name="address"
        v-model="restaurant.address"
        placeholder="Enter Restaurant Address"
      />
      <input
        type="text"
        name="contact"
        v-model="restaurant.contact"
        placeholder="Enter Contact Number"
      />
      <button v-on:click="handleUpdate" type="submit">Add</button>
    </div>
  </div>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";
export default {
  name: "Update",
  components: {
    Header,
  },
  data() {
    return {
      restaurant: {
        name: "",
        address: "",
        contact: "",
      },
    };
  },
  methods: {
    async handleUpdate() {
      let result = await axios.put(
        "http://localhost:3000/restaurant/" + this.$route.params.id,
        {
          name: this.restaurant.name,
          address: this.restaurant.address,
          contact: this.restaurant.contact,
        }
      );
      if (result.status == 200) {
          this.$router.push({name:"Home"})
      }
    },
  },
  async mounted() {
    let user = localStorage.getItem("user-Info");
    if (!user) {
      this.$router.push({ name: "login" });
    }
    let result = await axios.get(
      "http://localhost:3000/restaurant/" + this.$route.params.id
    );
    this.restaurant = result.data;
  },
};
</script>