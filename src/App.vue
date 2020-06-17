<template>
  <div id="app">
    <headerD class="header" />
    <addTodo @add-todo='addTodo' />
      <Todos v-bind:todos='Todos' @delTodo="deleteTodo" />
      <p v-if="Todos.length==0">No task avilable.</p>
  </div>
</template>

<script>
  import Todos from './components/Todo';
  import headerD from './components/layout/header';
  import addTodo from './components/addTodo';
  import axios from 'axios';

export default {
  name: 'App',
  components: {
    Todos,
    headerD,
    addTodo
  },
  methods: {
    deleteTodo(id){
      this.Todos = this.Todos.filter(todo => todo.id !=id);
    },
    addTodo(titleU){
      const newT = {
        id: this.Todos.length+1,
        title:titleU,
        completed:false
      }
      this.Todos = [...this.Todos,newT];
    }
  },
  data() {
    return {
     Todos: [
     ]
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => this.Todos = res.data)
    .catch( err => console.log(err));
  },
}

</script>

<style>
  *{
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    box-sizing: border-box;
    margin: 0%;
  }
  p{
    margin-left: 20%;
  }
  .header{
      padding: 5px;
      color: white;
      background: #34495E !important;
  }
</style>
