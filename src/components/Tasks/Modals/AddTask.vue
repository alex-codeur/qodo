<template>
  <q-card>
    <ModalHeader>Add Task</ModalHeader>
    <form @submit.prevent="submitForm">
      <q-card-section class="q-pt-none">
        <ModalTaskName v-model:name="taskToSubmit.name" ref="modalTaskName" />
        <ModalDueDate
          v-model:dueDate="taskToSubmit.dueDate"
          @clear="clearDueDate"
        />
        <ModalDueTime
          v-if="taskToSubmit.dueDate"
          v-model:dueTime="taskToSubmit.dueTime"
          @clear="clearDueDate"
        />
      </q-card-section>
      <ModalButtons />

      <!-- <pre>{{ taskToSubmit }}</pre> -->
    </form>
  </q-card>
</template>

<script>
import { mapActions } from "vuex";
import ModalHeader from "components/Tasks/Modals/Shared/ModalHeader.vue";
import ModalTaskName from "components/Tasks/Modals/Shared/ModalTaskName.vue";
import ModalDueDate from "components/Tasks/Modals/Shared/ModalDueDate.vue";
import ModalDueTime from "components/Tasks/Modals/Shared/ModalDueTime.vue";
import ModalButtons from "components/Tasks/Modals/Shared/ModalButtons.vue";

export default {
  components: {
    ModalHeader,
    ModalTaskName,
    ModalDueDate,
    ModalDueTime,
    ModalButtons,
  },
  data() {
    return {
      taskToSubmit: {
        name: "",
        dueDate: "",
        dueTime: "",
        completed: false,
      },
    };
  },
  methods: {
    ...mapActions("tasks", ["addTask"]),
    submitForm() {
      this.$refs.modalTaskName.$refs.name.validate();
      if (!this.$refs.modalTaskName.$refs.name.hasError) {
        this.submitTask();
      }
    },
    submitTask() {
      this.addTask(this.taskToSubmit);
      this.$emit("close");
    },
    clearDueDate() {
      (this.taskToSubmit.dueDate = ""), (this.taskToSubmit.dueTime = "");
    },
  },
};
</script>

<style>
</style>