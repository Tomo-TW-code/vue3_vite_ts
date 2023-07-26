<script setup lang="ts">
import TodoList from './components/TodoList.vue';
import { provide } from 'vue';
import { todos } from './useTodo'

provide('todos', todos)
// provide('addTodo', addTodo)
</script>

<template>
  <TodoList/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
