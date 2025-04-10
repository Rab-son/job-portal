<script setup>
// composition API
import { onMounted, ref } from 'vue';

const name = ref('John Doe');
const status = ref('active');
const tasks = ref(['Task One', 'Task Two', 'Task Three']);
const newTask = ref('')

const  toggleStatus = () => {
  if(status.value === 'active'){
    status.value = 'pending';
  }else if (status.value === 'pending'){
    status.value = 'inactive';
  }else{
    status.value = 'active';
  }
};

const addTask = () => {
  if(newTask.value.trim() !== ''){
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};

onMounted(async () => {
  try{
    const response = await fetch('https://jsonplaceholder.typicode.com/todos');
    const data = await response.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log('Error fetching tasks');
  }
});

</script>
<template>
  <h1>{{ message }}</h1><br>
  <p v-if="status === 'active'"> Message is active</p>
  <p v-else-if="status === 'pending'">Message is pending</p>
  <p v-else>Message is inactive</p><br>
  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask"/>
    <button type="submit">Submit</button>
  </form><br>

  <h1>Tasks</h1><br>
  <ul>
    <li v-for="task in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul><br>
   <button v-on:click="toggleStatus">Change Settings</button>
</template>

