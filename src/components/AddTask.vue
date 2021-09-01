<template>
    <form @submit="submitTask" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input type="text" name="task" v-model="text" placeholder="Add Task">
        </div>
        
        <div class="form-control">
            <label>Day & Time</label>
            <input type="text" name="day" v-model="day" placeholder="Add Day and Time">
        </div>
        
        <div class="form-control form-control-check">
            <label>Set Reminder</label>
            <input type="checkbox" name="Reminder" v-model="reminder">
        </div>
        
        <div class="form-control">
           
            <input type="submit" value="Save Task" class="btn btn-block" />
        </div>
        
    </form>
</template>

<script>
   export default {
       name: 'AddTask',
       data(){
           return {
                text : '',
                day : '',
                reminder : false
           }
       },
       methods:{
           submitTask(e){
             e.preventDefault();
             if(!this.text){
                 alert('Please add a task')
                 return
             }
             const newTask = {
                 id : Math.floor(Math.random() * 100000),
                 text : this.text,
                 day : this.day,
                 reminder : this.reminder
             }
             this.$emit('add-Task', newTask)
             this.text = ''
             this.day = ''
             this.reminder = false
           }
       }
   }
</script>

<style scoped>
    .add-form{
        margin-bottom: 40px;
    }
   .form-control{
       margin: 20px 0;
   }
    .form-control label{
        display: block;
    }
    .form-control input{
        width: 100%;
        height: 40px;
        margin: 5px;
        padding: 3px 7px;
        font-size: 17px;
    }
    .form-control-check{
        display: flex;
        align-content: center;
        justify-content: center;
    }
    .form-control-check label{
        flex: 1;
    }
    .form-control-check input{
        flex: 2;
        height: 20px;
    }
</style>