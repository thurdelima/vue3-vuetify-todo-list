<template>
  <v-text-field
    v-model="taskStore.titleTaskCreating"
    label="Add task"
    :rules="rules"
    @keyup.enter="taskStore.addTask"
  />

  <ListTask />
</template>

<script setup>
  import { onMounted } from 'vue';
  import ListTask from './ListTask.vue';
  import { useTaskStore } from '@/stores/task'

  const taskStore = useTaskStore();

  const rules = [
    (value) => {
      if (!value || value.length >= 5) return true;
      return "You must enter Task title with more then 5 characters.";
    },
  ];

  onMounted(() => {
    taskStore.getTasks();
  })


</script>
