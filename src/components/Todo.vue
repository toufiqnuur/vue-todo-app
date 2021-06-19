<template>
 <div class="todo-card">
   <div 
    class="card-text"
    :class="{ completed: completed }">
    <input 
      type="checkbox" 
      :checked="completed"
      @click="$emit('on-checked')"
    />
    {{ value }}
   </div>
   <div class="card-action">
    <button @click="$emit('on-delete')">
      Hapus
    </button>
   </div>
 </div>
</template>

<script>
export default {
  props: {
    value: String,
    completed: Boolean
  }
}
</script>

<style scoped>
.todo-card {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  background: #fff;
  box-shadow: 0 1px 5px #f0f0f0;
  padding: 1rem;
  border: 1px solid #f0f0f0;
  border-radius: .25rem;
  margin-bottom: 1rem;
}
.card-text {
  display: flex;
  align-items: center;
}
.card-text > input {
  margin-right: 1rem;
}
.completed {
  text-decoration: line-through;
}
</style>