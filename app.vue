<template>
  <div class="container mx-auto">
    <h1 class="text-3xl text-center font-mono font-bold">TO DO APP</h1>
    <div class="flex w-full">
      <div class="w-1/4">
        <input class="border" type="text" v-model="projectTitle" />
        <button class="border" @click="creatProject">Create</button>

        <h4 v-for="(project, index) in projects" @click="changeProject(index)">
          {{ project }}
        </h4>
      </div>
      <div class="w-3/4">
        <h2 class="text-2xl font-mono font-bold">
          tasks of {{ projects[selectedProject] }}
        </h2>
        <input class="border" type="text" v-model="taskTitle" />
        <button class="border" @click="createTask">Create</button>

        <h4 v-for="(task, index) in tasks">
          {{ task.projectIndex == selectedProject ? task.title: '' }}
        </h4>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const projects = ref<any>([]);
const tasks = ref<any>([]);
const taskTitle = ref("");
const projectTitle = ref("");
const selectedProject = ref(0);

const changeProject = (index: number) => {
  selectedProject.value = index;
};

const createTask = () => {
  tasks.value.push({
    title: taskTitle.value,
    projectIndex: selectedProject.value,
    isCompleted: false,
    isFav: false,
  });
  taskTitle.value = ""
};

const creatProject = () => {
  projects.value.push(projectTitle.value);
  projectTitle.value = ""

};
</script>
