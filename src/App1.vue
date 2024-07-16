<script>
// Options API
import { ref } from "vue";
export default {
  data() {
    return {
      name: "Pablo Sellares",
      status: "inactive",
      tasks: ["task one", "task two", "task three"],
      link: "https://google.com",
    };
  },
  methods: {
    toggleStatus() {
      if (this.status === "active") {
        this.status = "pending";
        // console.log(this.status);
      } else if (this.status === "pending") {
        this.status = "inactive";
        // console.log(this.status);
      } else {
        this.status = "active";
        // console.log(this.status);
      }
    },
  },
};
</script>

<template>
  <h1>{{ name }}</h1>
  <!-- <p v-if="status">User is active</p> -->
  <!-- <p v-else>User inactive</p> -->

  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>
  <!--  -->
  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <!-- <a v-bind:href="link">Google</a> -->
  <!-- <a :href="link">Google</a> -->
  <br />
  <!-- <button v-on:click="toggleStatus">Change status</button> -->
  <button @click="toggleStatus">Change status</button>
</template>

<style scoped>
button {
  padding: 16px 32px;
  background-color: hsla(160, 100%, 37%, 0.5);
  border: none;
  color: #fff;
  cursor: pointer;
  transition: background-color 125ms ease-in-out;
}

button:hover {
  background-color: hsla(160, 100%, 37%, 1);
}
</style>
