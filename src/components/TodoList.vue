<template>
  <CreateTodo @new-todo="addTodo($event)"/>
  <Todo 
    v-for="(todo, index) in todos"
    :value="todo.data"
    :completed="todo.completed"
    :key="index"
    @on-delete="removeTodo(index)"
    @on-checked="setIsComplete(index)"
  />
</template>

<script>
import CreateTodo from "./CreateTodo.vue"
import Todo from "./Todo.vue"

const KEY = "todo-vue",
      DB  = window.localStorage

export default {
  data() {
    return {
      todos: JSON.parse(DB.getItem(KEY)) || []
    }
  },
  methods: {
    addTodo: function(value) {
      this.todos.push({
        data: value,
        completed: false
      })
      DB.setItem(KEY, JSON.stringify(this.todos))
    },
    removeTodo: function(index) {
      this.todos.splice(index, 1)
      DB.setItem(KEY, JSON.stringify(this.todos))
    },
    setIsComplete: function(index) {
      this.todos[index]['completed'] = !this.todos[index]['completed']
      DB.setItem(KEY, JSON.stringify(this.todos))
    }
  },
  components: {
    CreateTodo,
    Todo
  }
}
</script>