<template>
  <div class="container">
    <h1 class="text-center mt-5">My Vue todo app</h1>
    <div class="d-flex">
      <input v-model="task" class="form-control" type="text" placeholder="nhập new task! " />
      <button v-on:click="submitTask" class="btn btn-warning">Submit</button>
    </div>
    <table class="table table-bordered">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Status</th>
          <th scope="col">#</th>
          <th scope="col">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task1,index) in tasks" :key="index" >
          <th>{{ task1.name}}</th>
          <td> {{task1.status}}</td>
          <td>
              <div v-on:click="editTask(index)">
                  <span class="fa fa-pen "> </span>
              </div>
          </td>
          <td>
              <div v-on:click="deleteTask(index)">
                  <span class="fa-solid fa-trash"> </span>
              </div>
          </td>
        </tr>
        
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
    data(){
        return{
            task:' '
            ,
            tasks:[
                {name:' code '
                ,
                status:'to-do'
                },
                {name:' shopping '
                ,
                status:'to-do'}
                ,
                {name:' game '
                ,
                status:'to-do'}
            ],
            editedTask:null
        }
    },
    methods:{
        submitTask: function(){
         if(this.task.length ==='0'){
             return;
         }
         if(this.editedTask === null){
             this.tasks.push({
             name:this.task
             ,
             status:'to-do',
         })
         }else{
             this.tasks[this.editedTask].name=this.task;
             this.editTask=null;
         }
         
         this.task='';
        },
        deleteTask: function(index){
            this.tasks.splice(index,1);
        },
        editTask: function(index){
           this.task=this.tasks[index].name;
           this.editedTask=index;
           
        }
    }

};
</script>

<style>
</style>