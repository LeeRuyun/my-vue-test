<script setup>
import AddTodo from './components/AddTodo.vue'
import TodoList from './components/TodoList.vue'
import {ref} from "vue"

const todos = ref([
  {
    id:1,
    text:"test"
  }
])
const handleAddTodo=(todo)=>{
  todos.value.push(todo)
}

const handleDeleteTodo=(todoId)=>{
  todos.value=todos.value.filter((todo)=>todo.id!==todoId)
}
const handleCompleteTodo=(todoId)=>{
  todos.value=todos.value.map((todo)=>todo.id === todoId ? {...todo,complete : !todo.complete}:todo)
}
</script>

<template>
  <div>
    <AddTodo @add-todo="handleAddTodo"/>
    <TodoList :todos="todos" @delete-todo="handleDeleteTodo" @complete-todo="handleCompleteTodo"/>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
