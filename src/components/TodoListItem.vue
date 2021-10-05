<template>
   <div>
        <span :id=index >{{ text }}</span><span> > </span>
        <button class="btn" @click="deleteTask">Delete</button>
        <button class="btn" @click="didTask" >Done</button>
    </div>
</template>

<script>
export default {
    name:'ToDoListItem',
    props: {
        text: String,
        index: Number
    },
    methods:{
        deleteTask:function(){
            this.$emit('select')
        },
        didTask:function(){
            this.$emit('done')
        }
    }
}
</script>

<style scoped>
    .active{
        text-decoration: line-through;
    }
    .btn{
        width: 100px;
        margin-left: 10px;
        margin-right:10px;
    }
</style>