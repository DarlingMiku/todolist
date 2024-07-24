<template>
    <div class="todo-list">
      <h1>Todo-list</h1>
      <TheCreateTodo
        @addTodo="addTodo"
        v-model="this.newTodo"
      />
      <ThePoints
        :todos = "this.todos"
        @remove = "removeTodo"
      />
    </div>
  </template>
  
  <script>
import TheCreateTodo from './TheCreateTodo.vue';
import ThePoints from './ThePoints.vue';

  export default {
    data() {
      return {
        newTodo: '',
        todo:{},
        todos: []
      };
    },

    methods: {
      addTodo() {
        if (this.newTodo.trim() !== '') {
          this.todo.index = this.todos.length + 1;
          this.todo.value = this.newTodo;
          this.todos.push(this.todo);
          this.newTodo = '';
          this.todo={}
        }
      },
      removeTodo(index) {
        this.todos = this.todos.filter((todo) => todo.index !== index)
      }
    },
    components:{
      ThePoints,
      TheCreateTodo
    }
  };
  </script>
  
  <style>
  .todo-list {
    display: flex;
    width: 600px;
    justify-content: center;
    flex-direction: column;
    margin: auto;
  }


</style>

