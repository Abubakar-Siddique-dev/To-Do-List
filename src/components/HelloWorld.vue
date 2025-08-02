<script setup>
import { ref } from 'vue';

const  tasks = ref([]);
const newTask = ref('');

const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
 };
const removeTask = (index) => {
   tasks.value.splice(index, 1);
};

</script>

<template>

  <h1 class="text-4xl text-gray-600 text-center font-semibold w-1/2 mx-auto mt-12 mb-6">To-Do List</h1>
  <div class="todo-app  border-1 border-gray-300 p-2 w-1/2 mx-auto rounded-xl drop-shadow-2xl">
    <div class="task-input  p-2 flex justify-evenly mt-2">
      <input class="w-md  px-4 py-2 border-1 border-black-200 rounded" type="text" v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task" />
      <button class="bg-green-400 px-2 py-1 rounded" @click="addTask">Add To Do</button>

  </div>

  <ul class="task-list p-2 mx-6">
    <li class="flex justify-evenly border-1 border-gray-300 rounded drop-shadow-sm  my-3 p-2" v-for="(task, index) in tasks" :key="index">
      <span class="w-md mr-2">{{ task }}</span>
      <button class="bg-red-400 px-2 py-1 h-fit rounded" @click="removeTask(index)">Remove</button>
    </li>
  </ul>
</div>
</template>



