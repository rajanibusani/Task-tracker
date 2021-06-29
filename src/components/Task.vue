<template>
  <div
    @click="onToggle(task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h3>
      {{ task.text }}
      <i @click="onDelete(task.id)" class="fas fa-times" />
    </h3>
    <h3>{{ task.day }}</h3>
  </div>
</template>
<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-task", id);
    },
    onToggle(id) {
      this.$emit("toggle-reminder", id);
    },
  },
};
</script>
<style scoped>
.task {
  /* background: #f4f4f4; */
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.fas {
  color: rgb(107, 39, 39);
}
.task.reminder {
  border-left: 5px solid rgb(10, 48, 10);
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>