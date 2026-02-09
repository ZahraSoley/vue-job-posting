<script>
export default {

  }

</script>

<template>

  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">user is active</p>
  <p v-else-if="status === 'pending'">user is pending</p>
  <p v-else>user is inactive</p>

  <h2>tasks</h2>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <!-- <a v-bind:href="link">GO To Google!</a> -->
  <a :href="link">GO To Google!</a>
  <br>

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
</style>


