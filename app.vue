<template>
  <div>
  <input type="text" v-model="taskname" placeholder="enter task">    
  <button @click="addtask">add task</button>

  <h4 v-for="task in tasks">{{ task }}</h4>
  </div>
</template>

<script setup lang="ts">

  const taskname = ref("")

  const tasks = ref([])

  const addtask = () => {
    tasks.value.push(taskname.value)
  }

</script>