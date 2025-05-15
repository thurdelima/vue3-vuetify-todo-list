<template>
  <div class="pa-4 text-center">
    <v-dialog v-model="taskStore.showDialogTaskFields" max-width="600" min-width="400">
      <v-card title="Edit Task">
        <template v-slot:text>
          <v-text-field v-model="props.task.title" label="Title"></v-text-field>
          <v-text-field v-model="props.task.description" label="Description"></v-text-field>
        </template>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn
            color="primary-darken-1"
            text="OK"
            variant="elevated"
            @click="taskStore.updateTask()"
          ></v-btn>

        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>


<script setup>
  import { defineProps } from "vue";
  import { useTaskStore } from '@/stores/task'

  const taskStore = useTaskStore();

  const props = defineProps({
    task: Object,
  });
</script>
