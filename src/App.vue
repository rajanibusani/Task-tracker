<template>
  <div class="container">
  <Header title="Task Tracker" @toggle-add-task="toggleAddTask" :toggleButton="showAddTask"/>
  <div v-show="showAddTask">
  <AddTask @add-task= "addTask"/>
  </div>
  <Tasks :tasks = "tasks" @delete-task = "deleteTask" @toggle-reminder = "toggleReminder"/>  
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";
export default {
  name: "App",  
  components: {  
    Header,
    Tasks,
    AddTask
  },
  data (){
    return {
      tasks : [],
      showAddTask:false,
    }    
  },
  methods:{
    deleteTask (id){     
      this.tasks = this.tasks.filter(task=>task.id !== id)
    },
    toggleReminder(id){       
      this.tasks = this.tasks.map(task=>{
        if(task.id === id){      
      return  {...task, reminder: !task.reminder} ;            
        }
        else{
          return task;
        }       
      })
    },
    addTask(newTask){      
      this.tasks = [...this.tasks, newTask]
      console.log(newTask)
    },
    toggleAddTask(){    
      this.showAddTask=!this.showAddTask
    }
  },
  created() {    
      this.tasks = [
        {
         id : 1,
         text : 'Doctors Appointment',
         day: 'july 2nd at 2.30pm',
         reminder: true,
        },
        {
         id : 2,
         text : 'Meeting at school',
         day: 'aug 9th at 8.30am',
         reminder: false,
        },
        {
         id : 3,
         text : 'Grocery Shopping',
         day: 'july 12th at 6.30pm',
         reminder: true,
        },
        {
           id: 4,
         text: "Collect the package from Føtex",
         day: 'july 22nd at 2.30pm',
         reminder: false,

        }
      ]
    }
};
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
  text-align: center;  
  background-image: url(https://miro.medium.com/max/2625/1*E7ELZyrme5bsu3m3QeiAzw.jpeg);
  background-repeat: no-repeat;  
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  /* border: 1px solid steelblue; */
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
