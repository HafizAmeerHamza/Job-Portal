<script>
  export default {
    data() {
      return {
        message: "hello world!",
        status: 'active',
        tasks: ['Task One', 'Task Two', 'Task Three'],
        link: "https://google.com"
      }
    },

    methods: {
      updateStatus() {
        if(this.status === 'active') {
          this.status = 'pending';
        } else if(this.status === 'pending') {
          this.status = 'inactive';
        } else {
          this.status = 'active';
        }
      }
    }
  }
</script>

<template>
  <h1>{{ message }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <ul> 
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <a :href="link">Link</a>
  <br>
  <!-- <button v-on:click="updateStatus">Click</button> -->
  <button @click="updateStatus">Click</button>
</template>

<style scoped></style>
