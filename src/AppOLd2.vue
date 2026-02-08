<script setup>
import { ref, onMounted } from "vue";

const name = ref("Zahra Soleymani");
const status = ref("active");
const link = ref("https://google.com");
const tasks = ref(["Task One", "Task Two", "Task Three"]);
const newTask = ref("");

const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
};

const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const removeTask = (task) => {
  tasks.value = tasks.value.filter((t) => t !== task);
};

onMounted(async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    if (!response.ok) {
      throw new Error(response.status);
    }
    const data = await response.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    alert(error);
  }
});
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">user is active</p>
  <p v-else-if="status === 'pending'">user is pending</p>
  <p v-else>user is inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">submit</button>
  </form>

  <h2>tasks</h2>
  <ul>
    <li v-for="task in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="removeTask(task)">X</button>
    </li>
  </ul>
  <!-- <a v-bind:href="link">GO To Google!</a> -->
  <a :href="link">GO To Google!</a>
  <br />

  <!-- <button v-on:click="toggleStatus">toggle user status</button> -->
  <button @click="toggleStatus">toggle user status</button>
</template>

<style>
h1 {
  font: 600;
}

h2 {
  text-transform: uppercase;
}

input {
  margin-left: 1rem;
}
</style>
