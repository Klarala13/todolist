<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
export default {
  name: 'app',
  components: {
    Todos
  },
  data(){
    return{
      todos:[
        {
          id: 1, 
          title: "ToDo One",
          completed: false
        },
        {
          id: 2, 
          title: "ToDo Two",
          completed: false
        },
        {
          id: 3, 
          title: "ToDo Three",
          completed: false
        }
      ]
    }
  },
  methods:{
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  }
}
</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.5;
}
</style>
