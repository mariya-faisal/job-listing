<!-- Options API -->

<script>
export default {
  data() {
    return {
      name: "Mariya",
      status: "active",
      tasks: ["task1", "task2", "task3"],
      link: "https://www.google.com",
    };
  },
  methods: {
    changeStatus() {
      this.status = this.status === "active" ? "inactive" : "active";
    },
  },
};
</script>

<template>
  <h1>Vue Job</h1>
  <h3>Name: {{ name }}</h3>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is Inactive</p>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <a :href="link">Google</a>

  <br />
  <button @click="changeStatus">Change Status</button>
</template>
