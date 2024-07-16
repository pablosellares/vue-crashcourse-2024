<script setup>
// Composition API
import { ref } from "vue";

const name = ref("Pablo Sellares");
const status = ref("active");
const tasks = ref(["task one", "task two", "task three"]);
const newTask = ref("");
const link = ref("https://google.com");

const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
    // console.log(status.value);
  } else if (status.value === "pending") {
    status.value = "inactive";
    // console.log(status.value);
  } else {
    status.value = "active";
    // console.log(status.value);
  }
};

const addTask = () => {
  if (newTask.value.trim != "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <h1>{{ name }}</h1>
  <!-- <p v-if="status">User is active</p> -->
  <!-- <p v-else>User inactive</p> -->

  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" name="newTask" id="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>
  <!-- <a v-bind:href="link">Google</a> -->
  <a :href="link">Google</a>
  <br />
  <!-- <button v-on:click="toggleStatus">Change status</button> -->
  <button @click="toggleStatus">Change status</button>
</template>

<style scoped>
/* button {
  padding: 16px 32px;
  background-color: hsla(160, 100%, 37%, 0.5);
  border: none;
  color: #fff;
  cursor: pointer;
  transition: background-color 125ms ease-in-out;
}

button:hover {
  background-color: hsla(160, 100%, 37%, 1);
} */
</style>
