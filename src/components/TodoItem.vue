<template>
    <div :class="{ isComplete: todo.completed }">
        <input type="checkbox" @change="toggleComplete">
        <span>{{ todo.title }}</span>
        <button @click="$emit('del-todo',todo.id)" class="btn">X</button>
    </div>
</template>

<script>
export default {
    name:'TodoItem',
    props: ['todo'],
    methods: {
        toggleComplete(){
            this.todo.completed = !this.todo.completed;
        }
    },
}
</script>

<style scoped>
    .isComplete{
        text-decoration: line-through;
    }

    span{
        margin-left: 10px;
        color: #34495E;
    }

    .btn{
        color: white;
        background: rgb(199, 54, 54);
        border-radius: 50%;
        border: none;
        float: right;
        cursor: pointer;
    }

    div{
        margin: 2%;
        width: 50%;
    }
</style>