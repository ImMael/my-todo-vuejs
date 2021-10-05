<template>
<div>
    <input v-model="title" placeholder="Entrez une tâche pour le todo-list" style="width:300px"/>
    <button @click="addTask" style="margin-left:10px"> Ajouter</button>
    <ul class="list">
        <li v-for="title, id in task" :key="id">
            <todo-list-item v-if="!title.done" :text=title.task :index=id @select="deleteTask(id)" @done="title.done = true"/>
            <todo-list-item-done v-else :text=title.task :index=id @select="deleteTask(id)" @done="title.done = false"/>
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
            this.task.push({task:this.title, done: false})
            console.log(this.title.id)
            console.log(this.task)
        },
        deleteTask:function(task){
            this.task.splice(task, 1)
        },
    },
}
</script>

<style scoped>

</style>