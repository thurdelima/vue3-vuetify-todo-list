<template>
  <div>
    <v-list
      lines="three"
      select-strategy="leaf"
    >
      <v-list-subheader>General</v-list-subheader>
      <v-list-item
        v-for="(task, index) in taskStore.tasks"
        :key="index"
        :subtitle="task.description"
        :title="task.title"
        :value="index"
        @click="taskStore.toggleDoneTask(index)"
      >
        <template v-slot:prepend="{ isSelected, select }">
          <v-list-item-action start>
            <v-checkbox-btn
              :model-value="task.done"
            />
          </v-list-item-action>
        </template>
        <template v-slot:append>
          <v-menu>
            <template v-slot:activator="{ props }">
              <v-btn color="grey-lighten" icon="mdi-dots-vertical" variant="text" v-bind="props"></v-btn>
            </template>
            <v-list>
              <v-list-item value="1" @click="taskStore.toggleEdit(index)">
                <v-list-item-title>Editar</v-list-item-title>
              </v-list-item>

              <v-list-item value="2" @click="taskStore.toggleDelete(index)">
                <v-list-item-title>Deletar</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </template>
      </v-list-item>
    </v-list>
    <DialogFieldsTask :task="taskStore.tasks[taskStore.indexTaskSelected]" />
    <DialogDeleteTask />
  </div>
</template>

<script setup>
  import DialogFieldsTask from '@/components/dialogs/DialogTaskFields.vue';
  import DialogDeleteTask from '@/components/dialogs/DialogDeleteTask.vue';
  import { useTaskStore } from '@/stores/task'

  const taskStore = useTaskStore();


</script>
