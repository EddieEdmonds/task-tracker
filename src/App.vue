<template>
  <div class="container">
    <Header title="Task Tracker"/>
    <Tasks 
      @delete-task="deleteTask" 
      @toggle-reminder="toggleReminder"
      :tasks="tasks" 
    />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data(){
    return {
      tasks: []
    }
  },
  methods:{
    deleteTask(id){
      if(confirm("Are you sure?")){
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id){
      if(confirm("Toggle reminder?")){
        this.tasks = this.tasks.map((task) => task.id == id ? {...task, reminder: !task.reminder} : task)
      }
    }
  },
  created(){
    this.tasks = [
      {
        id: 1, 
        text: 'Doctors Appt',
        day: 'March 1st - 2:30pm',
        reminder: true,
      },
      {
        id: 2, 
        text: 'Meeting at school',
        day: 'Feb 1st - 4:30pm',
        reminder: true,
      },
      {
        id: 3, 
        text: 'Oil Change',
        day: 'April 1st - 1:30pm',
        reminder: false,
      }
    ]
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
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
