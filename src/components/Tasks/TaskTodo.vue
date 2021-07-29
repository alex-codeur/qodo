<template>
  <div>
    <ListHeader bgColor="bg-orange-4">Todo</ListHeader>
    <q-list separator bordered>
      <Task
        v-for="(task, key) in tasksTodo"
        :key="key"
        :task="task"
        :id="key"
      />
    </q-list>
  </div>
</template>

<script>
import Task from "components/Tasks/Task.vue";
import ListHeader from "components/Shared/ListHeader.vue";
export default {
  props: ["tasksTodo"],
  components: {
    Task,
    ListHeader,
  },
};
</script>

<style>
</style>