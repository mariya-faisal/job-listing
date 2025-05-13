<!-- Composition API -->

<script setup>
import { ref } from "vue";

const name = ref("Mariya");
const status = ref("inactive");
const tasks = ref(["task1", "task2", "task3"]);
const newTask = ref("");

const changeStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
};

const addTask = () => {
  if (newTask.value !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <h1>Vue Job</h1>
  <h3>Name: {{ name }}</h3>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is Inactive</p>
  <br />
  <hr />
  <br />
  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input
      type="text"
      name="newTask"
      id="newTask"
      v-model="newTask"
      placeholder="Add a new task" />
    <button type="submit">Add Task</button>
  </form>
  <br />
  <hr />
  <br />
  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>

  <br />
  <button @click="changeStatus">Change Status</button>
</template>
