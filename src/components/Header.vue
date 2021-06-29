<template>
    <header>        
    <h1>{{title}}</h1>
    <Button 
    :text ="toggleButton ? 'Close' : 'Add Task' " 
    :color ="toggleButton ? 'red' : 'green' "  @btn-clcik="toggleAddTask()"/>
    </header>
</template>
<script>
import Button from './Button.vue';
export default {    
    name: 'Header',
    props :{
        title: String,
        toggleButton : Boolean,
    },
    methods:{
        
        toggleAddTask(){
          this.$emit("toggle-add-task")
        }
    },
    components:{
        Button,
        }
    }
</script>
<style scoped>
header{
display:flex;
justify-content: space-between;
align-items: center;
margin-bottom: 20px;
}
</style>
