<template>
<div>
    <input v-model="title" placeholder="Entrez une tâche pour le todo-list" style="width:300px"/>
    <button @click="addTask" style="margin-left:10px"> Ajouter</button>
    <ul class="list">
        <li v-for="title, id in task" :key="id">
            <todo-list-item v-if="!title.done" :text=title.task :index=id @delete="deleteTask(id)" @done="title.done = true"/>
            <todo-list-item-done v-else :text=title.task :index=id @delete="deleteTask(id)" @done="title.done = false"/>
        </li>
    </ul>
</div>
</template>

<script>
import TodoListItem from './TodoListItem.vue'
import TodoListItemDone from './TodoListItemDone.vue'
export default {
  components: {TodoListItem, TodoListItemDone},
    name:'ToDo-List',
    data: function(){
        return {
            task: [],
            title: ''
        }
    },
    methods:{
        addTask: function(){
            if(this.title !== ''){
                this.task.push({task:this.title, done: false})
                this.title = ''
            }
        },
        deleteTask:function(task){
            this.task.splice(task, 1)
        },
    },
}
</script>

<style>

input{
    border:none;
    height:25px;
    border-radius:10px;
    background-color:#F4F6F8;
    padding:10px;
}


button{
    border:none;
    background-color:#F4F6F8;
    padding: 15px;
    border-radius: 10px;
}
button:hover{
    background-color:#aaaaaa;
    cursor:pointer;
}

</style>