<template>
   <li>
      <span v-bind:class="{done: todo.completed}">
         <input type="checkbox" :checked="todo.completed"
            v-on:change="(todo.completed = !todo.completed), $emit('save-todo')">
         <strong>{{(index+1)}}</strong>
         {{todo.title}}
      </span>
      <button v-on:click="$emit('remove-todo', todo.id), $emit('save-todo')">&times;</button>
   </li>
</template>

<script>
export default {
   //filters: {
   //   uppercase(value) {
   //      console.log(value + '.-.')
   //      return value.toUpperCase()
   //   }
   //},
   props: {
      todo: {
         type: Object,
         required: true
      }, 
      index: Number
   },
   
}
</script>

<style scoped>
   li {
      border: 1px solid #303841;
      display: flex;
      justify-content: space-between;
      padding: .5rem 1rem;
      margin-bottom: 1rem;
   }
   strong {
      margin: 0 .5rem;
   }
   button {
      transition: .3s;
      transition-property: background;

      margin-left: 0.5rem;
      background: #303841;
      border: none;
      height: 20px;
      width: 20px;
      color: #fff;
      border-radius: 50%;
      font-weight: bold;
   }
   button:hover {
      background: #74F9FF;
   }
   span {
      text-align: justify;
      line-height: 20px;
   }
   .done {
      text-decoration: line-through;
   }
</style>