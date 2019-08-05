<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from "./components/layout/Header";
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";

import axios from "axios";

export default {
  name: 'app',
  components: {
    Header,
    AddTodo,
    Todos
  },
  data(){
    return{
      todos:[]
    }
  },
  methods:{
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
      .catch(err => console.error(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios.post("https://jsonplaceholder.typicode.com/todos", {
        title, 
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.error(err));
      
    }
  },
  created(){
    //Axios is an Http library to make get post req.
    axios.get("https://jsonplaceholder.typicode.com/todos?_limit=7")
    .then(res => this.todos = res.data)   
    .cath(err => console.error(err)); 
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
.btn{
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
