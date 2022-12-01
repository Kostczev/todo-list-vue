<template>
   <form @submit.prevent="onSubmit">
      <input type="text" v-model="title">
      <button type="submit">Create</button>
   </form>
</template>

<script>
export default {
   data() {
      return {
         title: ''
      }
   },
   methods: {
      onSubmit() {
         if (this.title.trim()) {
            const newTodo = {
               id: Date.now(),
               title: this.title,
               completed: false
            }
            this.$emit('add-todo', newTodo)
            this.$emit('save-todo')
            this.title = ''
         }
      }
   }
}
</script>

<style scoped>
   form {
      display: flex;
   }
   input {
      transition: .3s;
      transition-property: border, box-shadow;
      
      width: 100%;
      font-size: 16px;
      padding: 0.5rem;
      margin-right: 0.5rem;
      background: #3A4750;
      color: #fff;
      border: 2px solid #303841;
   }
   input:hover {
      border-color: #74F9FF;
   }
   input:focus-visible {
      outline: none;
      border-color: #74F9FF;
      box-shadow: 0 0 2px 0 #74F9FF;
   }
   button {
      transition: .3s;
      transition-property: border, color;

      background: #3A4750;
      color: #fff;
      border: 2px solid #303841;
      cursor: pointer;
   }
   button:hover{
      border-color: #74F9FF;
      color: #74F9FF;
   }
</style>