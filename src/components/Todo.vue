<template>
    <div class="todo-d">
        <h1 class="b-label">Todos</h1>
        <div v-for="todo in Todos" :key="todo.id">
            <!-- <h3>{{todo.title}}</h3> -->
            <TodoItem :todo='todo'  v-on:del-todo="$emit('delTodo',todo.id)" />
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem'
export default {
    name:'Todos',
    props:['Todos'],
    components:{
        TodoItem
    }
}
</script>

<style scoped>
    .b-label{
        border-left:20px solid #41B883;
        border-bottom: 3px solid #41B883;
        width: fit-content; 
        padding-left: 10px;
        color: #34495E;
    }
    .todo-d{
        margin: 3% 10%;
        padding: 5px;
    }
</style>