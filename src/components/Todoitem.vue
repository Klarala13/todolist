<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete">
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props:[
    "todo"
  ],
  methods: {
    markComplete(){
      // console.log("I'm complete!)
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Indie+Flower&display=swap');
  .todo-item{
    background: #f6f6f6;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
    font-family: 'Indie Flower', cursive;
  }
  .is-complete{
    text-decoration: line-through;
  }
  .del{
    background: red;
    color: white;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
  </style>