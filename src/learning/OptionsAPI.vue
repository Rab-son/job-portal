<script>
export default {
  //options API
  data() {
    return {
      message: 'Hello Vue 3!',
      status: 'pending',
      tasks: ['Task One', 'Task Two', 'Task Three'],
      link: 'https://google.com'
    }
  },
  methods: {
    toggleStatus() {
      if(this.status === 'active'){
        this.status = 'pending';
      }else if (this.status === 'pending'){
        this.status = 'inactive';
      }else{
        this.status = 'active';
      }
    }
  }
}
</script>
<template>
  <h1>{{ message }}</h1><br>
  <p v-if="status === 'active'"> Message is active</p>
  <p v-else-if="status === 'pending'">Message is pending</p>
  <p v-else>Message is inactive</p><br>
  <h1>Tasks</h1><br>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul><br>
  <!-- <a v-bind:href="link">Click for Google</a> -->
   <a :href="link">Google link</a><br>
   <button v-on:click="toggleStatus">Change Settings</button>
</template>

