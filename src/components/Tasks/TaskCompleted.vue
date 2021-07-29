<template>
  <div class="q-mt-lg">
    <ListHeader bgColor="bg-green-4">Completed</ListHeader>
    <q-list separator bordered>
      <task
        v-for="(task, key) in tasksCompleted"
        :key="key"
        :task="task"
        :id="key"
      />
    </q-list>
  </div>
</template>

<script>
import task from "components/Tasks/Task.vue";
import ListHeader from "components/Shared/ListHeader.vue";
export default {
  props: ["tasksCompleted"],
  components: {
    task,
    ListHeader,
  },
};
</script>

<style>
</style>