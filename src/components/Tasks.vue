<template>
  <div>
    <div v-for="task in tasks" :key="task.id">
      <Task
        @delete-task="$emit('delete', task.id)"
        @toggle-reminder="$emit('toggle', task.id)"
        :task="task"
      />
    </div>
  </div>
</template>

<script>
import Task from "./Task.vue";
export default {
  name: "Tasks",
  components: { Task },
  props: {
    tasks: {
      type: Array,
      default: [],
    },
  },
  emits: ["delete-task", "toggle-reminder"],
};
</script>

<style>
</style>