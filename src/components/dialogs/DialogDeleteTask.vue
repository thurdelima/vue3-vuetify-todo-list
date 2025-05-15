<template>
  <div class="pa-4 text-center">
    <v-dialog v-model="taskStore.showDialogDeleteTask" max-width="600" min-width="400">
      <v-card title="Delete Task">
        <template v-slot:text>
          Are you sure you want to delete task?
        </template>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn
            color="red-darken-1"
            text="No"
            variant="elevated"
            @click="taskStore.toggleDelete()"
          ></v-btn>

          <v-btn
            color="red-darken-1"
            text="Yes"
            variant="outlined"
            @click="taskStore.deleteTask()"
          ></v-btn>

        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script setup>
  import { useTaskStore } from '@/stores/task'

  const taskStore = useTaskStore();


</script>
