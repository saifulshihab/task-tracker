<template>
<div class="container">
  <Header :showAddform="showAddform" @show-add-task-form="showAddTaskForm" title="Task Tracker" />
  <div v-if="showAddform">
    <AddTask @add-task="addTask" />
  </div>
  <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
</div>
</template>

<script>
 import Header from './components/Header'
 import Tasks from './components/Tasks'
 import AddTask from './components/AddTask'
export default {
  name: 'App',
  components: {
     Header, Tasks, AddTask
  },
  data(){
    return {
      tasks: [],
      showAddform: false
    } 
  },
  methods: {
    deleteTask(id) {
      if(confirm('Are you sure?')){
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map(data => data.id === id ? {...data, reminder: !data.reminder} : data)
    },
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask]
    },
    showAddTaskForm() {
      this.showAddform = !this.showAddform
    }
  },
  created(){
    this.tasks = [
      {
        id: 1,
        text: 'Learning Django REST Framework',
        day: 'March 1',
        reminder: true
      },
      {
        id: 2,
        text: 'Learning Django REST Framework',
        day: 'March 1',
        reminder: true
      },
      {
        id: 3,
        text: 'Learning Django REST Framework',
        day: 'March 1',
        reminder: true
      }
    ]
  },
 
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
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
