<template>
  <q-page class="q-pa-md">
    <NoTasks
      v-if="!Object.keys(tasksTodo).length"
      @showAddTask="showAddTask = true"
    />

    <TaskTodo v-else :tasksTodo="tasksTodo" />

    <TaskCompleted
      v-if="Object.keys(tasksCompleted).length"
      :tasksCompleted="tasksCompleted"
    />

    <div class="absolute-bottom text-center q-mb-lg">
      <q-btn
        @click="showAddTask = true"
        round
        color="primary"
        size="24px"
        icon="add"
      />
    </div>

    <q-dialog v-model="showAddTask">
      <AddTask @close="showAddTask = false" />
    </q-dialog>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import { mapGetters } from "vuex";
import TaskTodo from "components/Tasks/TaskTodo.vue";
import NoTasks from "components/Tasks/NoTasks.vue";
import TaskCompleted from "components/Tasks/TaskCompleted.vue";
import AddTask from "components/Tasks/Modals/AddTask.vue";

export default defineComponent({
  data() {
    return {
      showAddTask: false,
    };
  },
  computed: {
    ...mapGetters("tasks", ["tasksTodo", "tasksCompleted"]),
  },
  components: {
    AddTask,
    TaskTodo,
    TaskCompleted,
    NoTasks,
  },
});
</script>

