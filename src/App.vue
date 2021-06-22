<template>
  <div id="app">
    <Header
      title="Track App"
      @toggle-add-task="toggleAddTask()"
      :toggleText="showAddTask"
    />
    <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks @delete="deleteTask" @toggle="toggleReminder" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

export default {
  name: "App",
  components: { Header, Tasks, AddTask },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    deleteTask(id) {
      if (confirm("Are you sure delete this task ?"))
        this.tasks = this.tasks.filter((task) => task.id !== id);
    },

    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },

    addTask(task) {
      this.tasks = [...this.tasks, task];
    },

    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        name: "do homeworks",
        day: "June 21st at 11:35am",
        reminder: true,
      },
      {
        id: 2,
        name: "play sports",
        day: "June 21st at 05:35pm",
        reminder: false,
      },
      {
        id: 3,
        name: "go to bed",
        day: "June 21st at 10:35pm",
        reminder: true,
      },
    ];
  },
  mounted() {
    if (localStorage.getItem("tasks")) {
      this.tasks = JSON.parse(localStorage.getItem("tasks"));
    }
  },
  watch: {
    tasks: {
      handler() {
        localStorage.setItem("tasks", JSON.stringify(this.tasks));
      },
      deep: true,
    },
  },
};
</script>

<style>
#app {
  border: 3px solid lightseagreen;
  border-radius: 10px;
  width: 1000px;
  margin: 50px auto;
  padding: 10px;
}
</style>
