<template>
  <div class="container">
    <Header
      @show-add-task="openAddTask"
      :isOpen="showAddTask"
      heading="Task Tracker"
    />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask"></AddTask>
    </div>
    <Tasks
      @delete-task="deleteTask"
      @toogle-reminder="changeReminder"
      :tasks="this.tasks"
    ></Tasks>
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    openAddTask() {
      this.showAddTask = !this.showAddTask;
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((r) => r.id !== id);
    },
    changeReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
      console.log("task-toogle", id);
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Buy Groceries",
        day: "March 1st @ 10:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Sell Groceries",
        day: "March 1st @ 11pm",
        reminder: false,
      },
      { id: 3, text: "Do Laundry", day: "March 1st @ 12pm", reminder: false },
      { id: 4, text: "Buy Funiture", day: "March 1st @ 13pm", reminder: true },
      { id: 5, text: "Read a book", day: "March 1st @ 14pm", reminder: false },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "Poppins", sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
