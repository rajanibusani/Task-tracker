
<template>
  <div :key="task.id" v-for="task in tasks" class="task-container">
    <Task
      :task="task"
      @delete-task="$emit('delete-task', task.id)"
      @toggle-reminder="$emit('toggle-reminder', task.id)"
    />   
  </div>
</template>
<script>
import Task from "./Task.vue";
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  emits: ["delete-task", "toggle-reminder"],
};
</script>
<style>
.task-container:nth-child(2n + 1) {
  background: linear-gradient(
    90deg,
    rgba(150, 64, 145, 0.5) 0%,
    rgba(250, 0, 135, 0.5) 100%
  );
}
.task-container:nth-child(2n + 2) {
  background: linear-gradient(
    90deg,
    rgba(72, 204, 67, 0.5) 0%,
    rgba(30, 77, 4, 0.904) 100%
  );
}
</style>