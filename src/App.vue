<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" 
    title="Task tracker"
    :showAddTask="showAddTask"></Header>

    <div v-show="showAddTask">
     <AddTask @add-task="addTask"></AddTask>
    </div>
    <Tasks @toggle-reminder="toggleReminder"
    @delete-task="deleteTask" :tasks="tasks"></Tasks>

  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
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
    toggleAddTask(){
      this.showAddTask = !this.showAddTask;
    },
    addTask(task){
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },

    toggleReminder(id){
      this.tasks = this.tasks.map( (task) => 
      task.id === id ? { ...task, reminder: !task.reminder } : task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Dinner to make",
        day: "March 3rd at 2pm",
        reminder: true,
      },

      {
        id: 2,
        text: "Cleaning",
        day: "March 3rd at 5pm",
        reminder: false,
      },

      {
        id: 3,
        text: "Appointment",
        day: "March 4th at 4pm",
        reminder: true,
      },
    ];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Kaisei+Opti&display=swap");

#app {
  font-family: "Kaisei Opti", serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  height: 20%;
  width: 50%;
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
