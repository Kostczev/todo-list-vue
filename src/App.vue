<template>
   <div id="app">
      <h1>Todo List</h1>
      <AddTodo
         @add-todo="addTodo"
         @save-todo="saveTodo"
      />
      <hr>
      <!--<Loader v-if="loading"/>-->
      <TodoList
         v-if="todos.length"
         v-bind:todos="todos"
         @remove-todo="removeTodo"
         @save-todo="saveTodo"
      />
      <p v-else>No todos</p>
   </div>
</template>

<script>
import TodoList from '@/components/TodoList';
import AddTodo from '@/components/AddTodo';
//import Loader from '@/components/Loader';
export default {
  name: 'App',
   data() {
      return {
         todos: JSON.parse(localStorage.getItem('todos') || '[]'),
         //todos: [],
         //loading: false
      }
   },
   //mounted() {
   //   fetch('https://jsonplaceholder.typicode.com/todos?_limit=50')
   //      .then(response => response.json())
   //      .then(json => {
   //         setTimeout(() => {
   //            this.todos = json
   //            this.loading = false
   //         }, 1000)
   //      })
   //},
   methods: {
      removeTodo(id) {
         this.todos = this.todos.filter(t => t.id !== id)
      },
      addTodo(todo) {
         this.todos.push(todo)
      },
      saveTodo() {
         localStorage.setItem('todos', JSON.stringify(this.todos))
      }
   },
   components: {
      TodoList, AddTodo
   },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #EEEEEE;
  margin-top: 60px;
  max-width: 900px;
  margin: 0 auto;
}
body {
   background: #3A4750;
   /*background: #303841;*/
}
</style>
