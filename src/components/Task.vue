<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <h5>
      {{ task.name }}
      <i class="fas fa-times" @click="$emit('delete-task', task.id)"></i>
    </h5>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: {
      type: Object,
      default: {},
    },
  },
};
</script>

<style scoped>
.task {
  background-color: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.reminder {
  border-left: 5px solid green;
}

.task h5 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.fas {
  color: red;
}
</style>