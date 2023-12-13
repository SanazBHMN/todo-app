<script setup>
import { ref, computed } from "vue";
import Header from "./components/Header.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

import d from "./data/data.json";

const todos = ref(d);

const handleAddTodo = (newTodoText) => {
  const newTodo = {
    id: Date.now(),
    text: newTodoText,
    isActive: true,
  };
  todos.value.push(newTodo);
};

const handleRemoveTodo = (todoId) => {
  todos.value = todos.value.filter((todo) => todo.id !== todoId);
};

const activeTodos = computed(() => todos.value.filter((todo) => todo.isActive));
</script>

<template>
  <main class="container">
    <Header />
    <TodoInput @add-todo="handleAddTodo" />
    <TodoList :todos="todos" @remove-todo="handleRemoveTodo" />
    <div>
      <small>{{ activeTodos.length }} items left</small>
    </div>
  </main>
</template>

<style scoped></style>
