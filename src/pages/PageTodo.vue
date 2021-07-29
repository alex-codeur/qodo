<template>
  <q-page class="q-pa-md">
    <q-list v-if="Object.keys(tasks).length" separator bordered>
      <task v-for="(task, key) in tasks" :key="key" :task="task" :id="key" />
    </q-list>

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
import task from "components/Tasks/Task.vue";
import AddTask from "components/Tasks/Modals/AddTask.vue";

export default defineComponent({
  data() {
    return {
      showAddTask: true,
    };
  },
  computed: {
    ...mapGetters("tasks", ["tasks"]),
  },
  components: {
    task,
    AddTask,
  },
});
</script>

