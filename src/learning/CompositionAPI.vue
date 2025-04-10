<script setup>
// composition API
import { ref } from 'vue';

const name = ref('John Doe');
const status = ref('active');
const tasks = ref(['Task One', 'Task Two', 'Task Three']);


const  toggleStatus = () => {
  if(status.value === 'active'){
    status.value = 'pending';
  }else if (status.value === 'pending'){
    status.value = 'inactive';
  }else{
    status.value = 'active';
  }
};


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
   <button v-on:click="toggleStatus">Change Settings</button>
</template>

