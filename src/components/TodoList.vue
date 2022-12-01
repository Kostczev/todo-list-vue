<template>
   <div>
      <ul>
         <TodoItem
            v-for="(todo, i) in todos" 
            v-bind:todo="todo"
            v-bind:index="i"
            v-on:remove-todo="removeTodo"
            v-on:save-todo="saveTodo"
         />
      </ul>
   </div>
</template>

<script>
import TodoItem from '@/components/TodoItem';
export default {
   props: ['todos'],
   components: {
      TodoItem
   },
   methods: {
      removeTodo(id) {
         this.$emit('remove-todo', id)
      },
      saveTodo() {
         this.$emit('save-todo')
      }
   }
}
</script>

<style scoped>
   ul {
      list-style: none;
      margin: 0;
      padding: 0;
   }
</style>