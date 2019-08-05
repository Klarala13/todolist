<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type ="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>

import uuid from "uuid";
export default {
  name: "AddTodo",
  data(){
    return{
      title: ''
    }
  },
  methods:{
    addTodo(e){
      e.preventDefault();
      //Stop default sending of form to a file, and then add the new Todo
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      }
      //send to parent element
      this.$emit("add-todo", newTodo);
    }
  }
}
</script>

<style scoped>
  form{
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
    height: 40px;
  }
  input[type="submit"] {
    flex: 2;
    height: 40px;
  }
</style>