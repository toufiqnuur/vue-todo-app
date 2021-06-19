<template>
  <form @submit.prevent="addTodo()">
    <input 
      v-model="newTodo"
      type="text" 
      placeholder="Type something here..." />
  </form>
</template>

<script>
  export default {
    data() {
      return {
        newTodo: ""
      }
    },
    methods: {
      addTodo: function() {
        if(this.newTodo.length) 
          this.$emit("new-todo", this.newTodo)
        this.newTodo = ""
        document.querySelector("input").blur()
      }
    }
  }
</script>

<style>
form {
  width: 100%;
  margin-bottom: 1.5rem;
  display: flex;
}
input[type="text"] {
  font-size: 1rem;
  padding: 1rem;
  border-radius: .25rem;
  border: 1px solid #f0f0f0;
  box-shadow: 0 1px 5px #f0f0f0;
  margin-right: 1rem;
}
</style>